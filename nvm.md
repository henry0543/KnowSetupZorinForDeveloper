Here is the complete content for your single `README.md` file. 

```markdown
# NVM Installation Guide for Zorin OS & Ubuntu

[![Ubuntu](https://img.shields.io/badge/OS-Ubuntu%20/%20Zorin%20OS-E95420?logo=ubuntu&logoColor=white)](https://ubuntu.com/)
[![Node.js](https://img.shields.io/badge/Node.js-Managed%20via%20NVM-339933?logo=node.js&logoColor=white)](https://nodejs.org/)

A comprehensive, step-by-step guide to installing and configuring **Node Version Manager (nvm)** on Zorin OS and Ubuntu-based distributions.

---

## 📑 Table of Contents
- [Prerequisites](#-prerequisites)
- [Installation](#-installation)
- [Basic Usage](#-basic-usage)
- [Troubleshooting](#-troubleshooting)
- [Uninstallation](#-uninstallation)

---

## 📋 Prerequisites

Before installing `nvm`, ensure your system has the necessary build tools, `git`, and `curl`.

Open your terminal (`Ctrl` + `Alt` + `T`) and run:

```bash
sudo apt update
sudo apt install curl build-essential libssl-dev git -y
```

---

## 🚀 Installation

### 1. Download and Run the Install Script
Use `curl` to download the official installation script. 

> **Note:** Check the [nvm GitHub releases](https://github.com/nvm-sh/nvm/releases) to ensure you are using the latest version number. Replace `v0.40.1` below if a newer version exists.

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
```

### 2. Activate nvm in Your Current Shell
The script automatically appends the necessary configuration to your shell profile (`~/.bashrc`, `~/.zshrc`, or `~/.profile`). 

To start using `nvm` immediately without restarting your terminal, source your profile:

**For Bash (Default in Zorin/Ubuntu):**
```bash
source ~/.bashrc
```

**For Zsh (If you use Zsh):**
```bash
source ~/.zshrc
```

### 3. Verify the Installation
Confirm that `nvm` is installed and accessible:

```bash
nvm --version
```
*Expected output: `0.40.1` (or your installed version).*

---

## 💻 Basic Usage

### Install Node.js
```bash
# Install the latest Long Term Support (LTS) version (Recommended)
nvm install --lts

# Install the absolute latest version
nvm install node
```

### Set a Default Version
Set a specific version to be used automatically every time you open a new terminal:
```bash
nvm alias default 20.11.0
```

### Switch Between Versions
```bash
# Use a specific installed version
nvm use 18.19.0

# Use the latest installed version
nvm use node
```

### View Available Versions
```bash
# List versions installed on your local machine
nvm ls

# List all available versions on the remote Node.js server
nvm ls-remote
```

---

## 🛠 Troubleshooting

### Issue: `nvm: command not found`
**Fix:** Close and reopen your terminal, or manually source your profile:
```bash
source ~/.bashrc  # OR source ~/.zshrc OR source ~/.profile
```

### Issue: Permission denied when running Node/npm globally
**Cause:** Using the system's default Node.js (installed via `apt`) alongside `nvm` can cause path conflicts.
**Fix:** Ensure you are using the `nvm` version of Node, not the system version:
```bash
which node
# The output should be inside your ~/.nvm directory, NOT /usr/bin/node
```

---

## 🗑 Uninstallation

If you need to remove `nvm` completely:

1. Remove the `nvm` directory:
   ```bash
   rm -rf ~/.nvm
   ```
2. Remove the configuration lines from your shell profile (`~/.bashrc`, `~/.zshrc`, `~/.profile`, etc.). Look for and delete these lines:
   ```bash
   export NVM_DIR="$HOME/.nvm"
   [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
   [ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"
   ```

---

## 📚 Resources

- [Official nvm GitHub Repository](https://github.com/nvm-sh/nvm)
- [Node.js Official Website](https://nodejs.org/)
```

Here is the **single, all-in-one command** to install prerequisites, install nvm, activate it in your current terminal, and install the latest LTS version of Node.js. 

Just copy and paste this entire block into your Zorin/Ubuntu terminal and press Enter:

```bash
sudo apt update && sudo apt install -y curl git build-essential libssl-dev && curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash && export NVM_DIR="$HOME/.nvm" && [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" && nvm install --lts
```

*(It will ask for your password once for `sudo`, then handle the rest automatically. When it finishes, Node.js and nvm are ready to use).*
