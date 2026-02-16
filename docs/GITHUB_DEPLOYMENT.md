# GitHub Deployment Guide

Version control and backup workflow for the Home Assistant dashboard configuration.

---

## Repository Structure

```
dynamic_dashboard_v1/
├── .gitignore                    # Security-aware ignore rules
├── .github/
│   └── FUNDING.yml               # Sponsorship configuration
├── README.md                     # Project overview and features
├── DEPLOYMENT.md                 # Step-by-step deployment guide
├── HACS_DEPENDENCIES.md          # Complete HACS card list
├── VALIDATION_REPORT.md          # Implementation validation status
├── dashboard.yaml                # Original full dashboard YAML
├── config/
│   ├── .gitignore                # Excludes ha-repos from config
│   ├── configuration.yaml        # Light groups & template sensors
│   └── dashboards/
│       ├── mobile-dashboard.yaml       # Adapted dashboard (deploy this)
│       ├── mobile-dashboard.yaml.backup # Pre-adaptation backup
│       ├── DASHBOARD_README.md         # Dashboard documentation
│       ├── SENSOR_INTEGRATION_GUIDE.md # Sensor setup guide
│       ├── STRUCTURE_MAP.md            # View structure analysis
│       └── CHANGELOG.md               # Change tracking
├── assets/                       # Dashboard card code examples
├── template sensor/              # Template sensor configurations
├── hue asset/                    # Hue scene automation files
│   └── scene images/             # Hue scene preview images
├── wallpaper/                    # Dashboard wallpaper files
└── docs/
    ├── GITHUB_DEPLOYMENT.md      # This file
    ├── TESTING_CHECKLIST.md      # Validation procedures
    └── MISSING_INTEGRATIONS.md   # Optional integrations guide
```

---

## Initial Setup

### Option A: Fork the Repository (Recommended)

Forking preserves the connection to the upstream repository, allowing you to receive future updates.

1. **Fork on GitHub:**
   - Navigate to the repository on GitHub
   - Click the **Fork** button (top right)
   - Select your account as the destination

2. **Clone your fork:**
   ```bash
   git clone https://github.com/YOUR_USERNAME/dynamic_dashboard_v1.git
   cd dynamic_dashboard_v1
   ```

3. **Add upstream remote** (for future updates):
   ```bash
   git remote add upstream https://github.com/ORIGINAL_OWNER/dynamic_dashboard_v1.git
   ```

4. **Verify remotes:**
   ```bash
   git remote -v
   # origin    https://github.com/YOUR_USERNAME/dynamic_dashboard_v1.git (fetch)
   # origin    https://github.com/YOUR_USERNAME/dynamic_dashboard_v1.git (push)
   # upstream  https://github.com/ORIGINAL_OWNER/dynamic_dashboard_v1.git (fetch)
   # upstream  https://github.com/ORIGINAL_OWNER/dynamic_dashboard_v1.git (push)
   ```

### Option B: Clone Directly

If you do not need upstream updates:

```bash
git clone https://github.com/OWNER/dynamic_dashboard_v1.git
cd dynamic_dashboard_v1
```

### Option C: Use Within Home Assistant (VSCode Addon)

1. Install the **Visual Studio Code** addon from the Add-on Store
2. Open VSCode from the sidebar
3. Open Terminal within VSCode (Ctrl+`)
4. Navigate to or clone the repository:
   ```bash
   cd /config
   git clone https://github.com/YOUR_USERNAME/dynamic_dashboard_v1.git
   ```

---

## Secrets Management

### What is Excluded from Git

The `.gitignore` file is pre-configured to exclude sensitive files:

```
# Security & Secrets
secrets.yaml          # API keys, passwords, tokens
.storage/             # HA internal storage (includes auth tokens)
.cloud/               # Nabu Casa cloud credentials

# Database & Logs
home-assistant_v2.db  # Full state history database
home-assistant.log    # May contain sensitive entity data

# Runtime
__pycache__/          # Python cache files
blueprints/           # Downloaded automations
deps/                 # Python dependencies

# Local development
ha-repos/             # Cloned HACS card source repositories
.venv/                # Python virtual environments
```

### Creating secrets.yaml

If your dashboard references secrets:

```yaml
# /config/secrets.yaml - NEVER commit this file
ha_url: "http://192.168.1.100:8123"
latitude: "your_latitude"
longitude: "your_longitude"
elevation: "your_elevation"
```

### Verifying Secrets Are Not Tracked

Before any commit, verify secrets are not staged:

```bash
# Check what would be committed
git status

# Verify secrets.yaml is not tracked
git ls-files --cached | grep -i secret
# Should return nothing

# If secrets.yaml was accidentally added:
git rm --cached secrets.yaml
git commit -m "Remove secrets.yaml from tracking"
```

---

## Git Workflow

### Making Changes

1. **Create a branch for your changes:**
   ```bash
   git checkout -b feature/add-bedroom-sensors
   ```

2. **Make your changes** to dashboard YAML, configuration, etc.

3. **Verify nothing sensitive is staged:**
   ```bash
   git status
   git diff --cached
   ```

4. **Commit with a descriptive message:**
   ```bash
   git add config/dashboards/mobile-dashboard.yaml
   git commit -m "Enable bedroom temperature and humidity sensors"
   ```

5. **Push to your repository:**
   ```bash
   git push origin feature/add-bedroom-sensors
   ```

6. **Merge to main when tested:**
   ```bash
   git checkout main
   git merge feature/add-bedroom-sensors
   git push origin main
   ```

### Commit Best Practices

**Message format:**
```
<type>: <short description>

<optional longer description>
```

**Types:**
- `feat:` - New feature or card added
- `fix:` - Bug fix (entity name correction, YAML syntax fix)
- `config:` - Configuration change (groups, sensors, integrations)
- `style:` - Visual/styling changes (card-mod CSS, theme adjustments)
- `docs:` - Documentation updates
- `refactor:` - Code restructuring without functionality change

**Examples:**
```bash
git commit -m "feat: enable bedroom motion sensor cards"
git commit -m "fix: correct kitchen light group entity names"
git commit -m "config: add temperature sensor template"
git commit -m "style: adjust room card gradient colors"
```

### Pulling Upstream Updates (Fork Only)

If you forked the repository and want to get updates:

```bash
# Fetch upstream changes
git fetch upstream

# Merge upstream main into your main
git checkout main
git merge upstream/main

# Resolve any conflicts in your dashboard customizations
# Then push to your fork
git push origin main
```

---

## Using the VSCode Server Addon

The VSCode Server addon provides a full IDE experience within Home Assistant.

### Setup

1. **Install the addon:**
   - Settings > Add-ons > Add-on Store
   - Search for "Visual Studio Code"
   - Click Install, then Start

2. **Configure git credentials:**
   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "your.email@example.com"
   ```

3. **Set up SSH keys** (for push access):
   ```bash
   ssh-keygen -t ed25519 -C "your.email@example.com"
   cat ~/.ssh/id_ed25519.pub
   # Add this key to GitHub: Settings > SSH and GPG keys > New SSH key
   ```

### Useful VSCode Extensions

- **YAML** - Syntax highlighting and validation
- **Home Assistant Config Helper** - Entity ID autocomplete
- **GitLens** - Enhanced git integration

### Working with YAML in VSCode

- Use **Ctrl+Shift+P** > "Format Document" to fix indentation
- Enable "Files: Trim Trailing Whitespace" in settings
- Set tab size to 2 spaces for YAML files

---

## Backup Strategy

### Automated Backups

Create a simple backup script:

```bash
#!/bin/bash
# backup-dashboard.sh
DATE=$(date +%Y%m%d_%H%M%S)
cp config/dashboards/mobile-dashboard.yaml \
   config/dashboards/backups/mobile-dashboard_${DATE}.yaml
echo "Backup created: mobile-dashboard_${DATE}.yaml"
```

### Git-Based Backup

Every commit serves as a backup point. Tag important milestones:

```bash
# Tag a known-good state
git tag -a v1.0-pre-sensors -m "Working dashboard before sensor integration"

# Tag after sensor integration
git tag -a v1.1-sensors-active -m "All sensors integrated and tested"

# List all tags
git tag -l

# Restore to a tagged version if needed
git checkout v1.0-pre-sensors -- config/dashboards/mobile-dashboard.yaml
```

### Pre-Change Backup

Before making significant changes:

```bash
# Create a backup branch
git checkout -b backup/before-climate-integration
git checkout main

# If something goes wrong, restore from backup branch
git checkout backup/before-climate-integration -- config/dashboards/mobile-dashboard.yaml
```

---

## Troubleshooting

### Common Git Issues

**Problem: Accidentally committed secrets.yaml**
```bash
# Remove from tracking (keeps file locally)
git rm --cached secrets.yaml
git commit -m "Remove secrets from tracking"

# If pushed, you should rotate any exposed credentials
# Then force push to remove from history (use with caution)
git filter-branch --force --index-filter \
  'git rm --cached --ignore-unmatch secrets.yaml' HEAD
git push --force
```

**Problem: Merge conflicts in dashboard YAML**
```bash
# View conflicting files
git status

# Open the file and look for conflict markers:
# <<<<<<< HEAD
# (your changes)
# =======
# (incoming changes)
# >>>>>>> branch-name

# Manually resolve, then:
git add config/dashboards/mobile-dashboard.yaml
git commit -m "Resolve merge conflict in dashboard"
```

**Problem: Large file warnings**
```bash
# The dashboard YAML is ~500KB which is normal
# If git warns about file size, it is expected
# Consider adding to .gitattributes if needed:
echo "*.yaml diff" >> .gitattributes
```

**Problem: Permission denied on push**
```bash
# Verify remote URL
git remote -v

# Switch to SSH if using HTTPS:
git remote set-url origin git@github.com:YOUR_USERNAME/dynamic_dashboard_v1.git

# Or use a personal access token with HTTPS
```
