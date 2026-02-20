# Installation Guide

## Prerequisites

Before installing the Threat Modeling Power, ensure you have:

- **Kiro IDE** installed and configured
- **Python 3.10+** installed
- **pipenv** for Python dependency management
- **SQLite3** (usually pre-installed on most systems)
- **Git** for cloning the repository

## Installation Methods

### Method 1: Install via Git URL (Recommended)

The easiest way to install this power is directly from the git repository:

```bash
# Install the power
kiro powers install https://github.com/YOUR_USERNAME/threat-modeling-power.git
```

Kiro will automatically:

1. Clone the repository to `~/.kiro/powers/threat-modeling/`
2. Run `pipenv install` to set up dependencies
3. Register the power for use

### Method 2: Manual Installation

If you prefer manual installation or want to contribute:

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/threat-modeling-power.git
cd threat-modeling-power

# Install Python dependencies
pipenv install

# Link to Kiro powers directory (optional)
ln -s $(pwd) ~/.kiro/powers/threat-modeling
```

## Verify Installation

After installation, verify the power is available:

```bash
# List installed powers
kiro powers list

# You should see "threat-modeling" in the list
```

Or in Kiro IDE, type:

```
List my installed powers
```

## Post-Installation Setup

### 1. Test Knowledge Base Access

Verify the knowledge base is accessible:

```bash
cd ~/.kiro/powers/threat-modeling
./kb --stride spoofing
```

You should see STRIDE threat information for the Spoofing category.

### 2. Test Module Discovery Script

Test the module discovery script:

```bash
cd ~/.kiro/powers/threat-modeling
python scripts/module_discovery.py . --p1-discovery --summary-only
```

This should output project structure information.

### 3. Verify SQLite Database

Check that the knowledge base database exists:

```bash
ls -lh ~/.kiro/powers/threat-modeling/knowledge/security_kb.sqlite
```

Expected size: ~18-26 MB

## Troubleshooting

### Issue: "pipenv: command not found"

Install pipenv:

```bash
# Using pip
pip install --user pipenv

# Using homebrew (macOS)
brew install pipenv

# Using apt (Ubuntu/Debian)
sudo apt install pipenv
```

### Issue: "Python version mismatch"

Ensure Python 3.10+ is installed:

```bash
python --version
# or
python3 --version
```

If needed, install Python 3.10+:

- macOS: `brew install python@3.10`
- Ubuntu: `sudo apt install python3.10`
- Windows: Download from python.org

### Issue: "Knowledge base not found"

The knowledge base files should be in the `knowledge/` directory. If missing:

```bash
cd ~/.kiro/powers/threat-modeling
ls -la knowledge/
```

You should see:

- `security_kb.sqlite` (~18 MB)
- Various `.yaml` files
- `security-controls/` directory

### Issue: "Permission denied" when running scripts

Make scripts executable:

```bash
cd ~/.kiro/powers/threat-modeling
chmod +x kb
chmod +x scripts/*.py
```

## Updating the Power

To update to the latest version:

```bash
# If installed via git URL
kiro powers update threat-modeling

# If manually installed
cd ~/.kiro/powers/threat-modeling
git pull origin main
pipenv install --deploy
```

## Uninstallation

To remove the power:

```bash
# Using Kiro
kiro powers uninstall threat-modeling

# Manual removal
rm -rf ~/.kiro/powers/threat-modeling
```

## Next Steps

Once installed, see:

- [USAGE.md](USAGE.md) - How to use the power
- [POWER.md](POWER.md) - Power capabilities and features
- [README.md](README.md) - Complete documentation

## Getting Help

If you encounter issues:

1. Check the [Troubleshooting](#troubleshooting) section above
2. Review the [GitHub Issues](https://github.com/YOUR_USERNAME/threat-modeling-power/issues)
3. Open a new issue with:
   - Your OS and Python version
   - Kiro version
   - Error messages
   - Steps to reproduce
