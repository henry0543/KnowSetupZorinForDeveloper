```markdown
# Node Version Manager (nvm) Cheat Sheet & Setup Guide

[![OS - Ubuntu / Zorin OS](https://img.shields.io/badge/OS-Ubuntu%20%7C%20Zorin%20OS-E95420?logo=ubuntu&logoColor=white)](https://ubuntu.com/)
[![Shell - Bash / Zsh](https://img.shields.io/badge/Shell-Bash%20%7C%20Zsh-4EAA25?logo=gnu-bash&logoColor=white)](https://www.gnu.org/software/bash/)
[![Node.js - Version Management](https://img.shields.io/badge/Node.js-NVM%20Managed-339933?logo=node.js&logoColor=white)](https://nodejs.org/)
[![License - MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

A clean reference guide for installing, configuring, and working with **Node Version Manager (`nvm`)** on Zorin OS, Ubuntu, and Debian derivatives.

---

## ⚡ Quick Start (One-Liner)

To update repositories, install build dependencies, fetch `nvm`, configure your current shell, and install the latest Node.js LTS release in a single pass:

```bash
sudo apt update && sudo apt install -y curl git build-essential libssl-dev && \
curl -o- [https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh](https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh) | bash && \
export NVM_DIR="$HOME/.nvm" && \
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" && \
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion" && \
nvm install --lts

```

---

## 📋 Step-by-Step Installation

### 1. Install System Dependencies

`nvm` builds some Node releases from source and requires standard fetch/build utilities:

```bash
sudo apt update
sudo apt install -y curl git build-essential libssl-dev

```

### 2. Run the Official Installer Script

Fetch and execute the install script from the [official repository](https://github.com/nvm-sh/nvm?utm_source=gemini):

```bash
curl -o- [https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh](https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh) | bash

```

> **Tip:** Replace `v0.40.1` with the latest tag from the [nvm releases page](https://github.com/nvm-sh/nvm/releases?utm_source=gemini) if a newer version is available.

### 3. Load nvm into Your Current Session

The installer adds the required environment variables to `~/.bashrc`, `~/.zshrc`, or `~/.profile`. Load them immediately:

```bash
# For Bash (default on Ubuntu / Zorin):
source ~/.bashrc

# For Zsh:
source ~/.zshrc

```

### 4. Verify Installation

Ensure the shell recognizes the function:

```bash
command -v nvm
# Outputs: nvm

nvm --version
# Outputs: 0.40.1 (or your installed version)

```

---

## 💻 Everyday Commands

| Task | Command | Notes |
| --- | --- | --- |
| **Install LTS** | `nvm install --lts` | Best for stability and production parity |
| **Install Latest** | `nvm install node` | Installs the newest active Node release |
| **Install Specific Version** | `nvm install 20.18.0` | Target an exact version |
| **Set System Default** | `nvm alias default 20.18.0` | Persists across terminal sessions |
| **Switch Active Version** | `nvm use 18.20.4` | Changes version for current session only |
| **List Installed Versions** | `nvm ls` | Shows all locally installed versions |
| **List Available Remotes** | `nvm ls-remote --lts` | Shows all available remote LTS releases |
| **Check Current Version** | `nvm current` | Displays currently active version |
| **Uninstall a Version** | `nvm uninstall 16.20.2` | Removes an unneeded local version |

---

## ⚙️ Advanced Workflows

### Automatic Version Switching per Project (`.nvmrc`)

Pin specific Node versions for different codebases by adding an `.nvmrc` file to the root of your project:

```bash
# Create the file with the target version
echo "20.18.0" > .nvmrc

# Tell nvm to read the file and activate that version
nvm use

# Install the version declared in .nvmrc if missing
nvm install

```

### Handling Global Packages Across Upgrades

Reinstall all globally installed npm packages from an older Node version into a new one:

```bash
nvm install 22.0.0 --reinstall-packages-from=20.18.0

```

---

## 🛠️ Troubleshooting

### 1. `nvm: command not found`

If opening a new terminal tab does not recognize `nvm`, ensure these lines exist inside your `~/.bashrc` or `~/.zshrc`:

```bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"

```

Save the file and run `source ~/.bashrc` (or reopen your terminal).

### 2. Path Conflicts with System Node (`/usr/bin/node`)

If Node commands throw permission errors or resolve to the wrong binary, check which binary has priority in your `$PATH`:

```bash
which node

```

* **Correct output:** `/home/<username>/.nvm/versions/node/vX.X.X/bin/node`
* **Conflict output:** `/usr/bin/node` or `/usr/local/bin/node`

If pointing to `/usr/bin/node`, remove the system package to avoid conflicts:

```bash
sudo apt remove --purge nodejs npm

```

---

## 🧹 Complete Uninstallation

To remove `nvm` and all installed Node runtimes:

```bash
# 1. Delete the installation directory
rm -rf "$HOME/.nvm"

# 2. Clean shell profiles
# Open ~/.bashrc, ~/.zshrc, or ~/.profile and delete the NVM export block:
nano ~/.bashrc

```

Remove:

```bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"

```

Then reload:

```bash
source ~/.bashrc

```

```

```
