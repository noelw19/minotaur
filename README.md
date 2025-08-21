# 🐂 Minotaur  

Minotaur is a lightweight tool designed to simplify multi-server management.  
It was built out of frustration with how slow **RDM** is and the need to constantly juggle between **WinSCP** and SSH. Instead of switching between multiple applications, Minotaur combines everything into a single, efficient workflow.  

![License](https://img.shields.io/badge/license-MIT-blue.svg)  
![Shell](https://img.shields.io/badge/shell-bash-green.svg)  
![PRs](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)  

---

## 📑 Table of Contents  

- [Features](#features)  
- [Installation](#installation)  
- [Authentication](#authentication)  
- [Workflow](#workflow)  
- [Usage](#usage)  
- [Configuration](#-configuration)  
- [Quick Start](#quick-start)  
- [Contributing](#contributing)  
- [License](#license)  

---

<a name="features"></a>
## 🚀 Features


- Manage up to **three configuration files** for flexible setups.  
- Connect to **multiple servers at once** using **tags** and **tmux**.  
- Copy **single or multiple files** to multiple servers simultaneously.  
- Quickly connect to a server using either its **IP address** or its **configured name**.  

---

<a name="installation"></a>
## ⚙️ Installation  

Clone the repository and add Minotaur to your `$PATH`:  

```bash
git clone https://github.com/yourname/minotaur.git
cd minotaur
export PATH=$PATH:$(pwd)
```

For persistent use, add this line to your `.bash_profile` or `.zshrc`:  

```bash
export PATH=$PATH:~/path/to/minotaur/
```

---

<a name="authentication"></a>
## 🔐 Authentication  

- **SSH key support** is built-in, allowing secure, passwordless logins.  
- If no key is provided, you’ll be prompted for your password.  
- Per-server usernames can override the default/root username in your configs when needed.  

---

<a name="workflow"></a>
## 🖥 Workflow  

When you’re done, simply exit the session with:  

```bash
ctrl + b > :kill-session
```

This closes the entire tmux session—no need to `exit` a hundred times.  

---

<a name="usage"></a>
## 📘 Usage  

### Copy Files  
Copy a file or directory to all servers with a given tag:  

```bash
minotaur -c -f ./path/to/fileOrDir -t tag
```

### Connect via SSH  
SSH into all servers with a given tag:  

```bash
minotaur -s -t tag
```

SSH into servers with a tag but in a specific environment:  

```bash
minotaur -s -t tag -e dev
```

### Show Current Environment Config  
```bash
minotaur -p
```

### Show tmux Help  
```bash
minotaur -z
```

---

<a name="configuration"></a>
## ⚡ Configuration  

Minotaur supports three environment-specific config files:  

- `conf-dev.json` → Development  
- `conf-pre.json` → Pre-production  
- `conf-prod.json` → Production  

### Example Config (`conf-dev.json`)  

```json
{
  "sshKey": "~/.ssh/user_ssh_key",
  "username": "john.doe",
  "boxes": {
    "backend": {
      "ip": "10.0.4.10",
      "tag": "back",
      "username": "admin"
    },
    "backend1": {
      "ip": "10.0.4.11",
      "tag": "back"
    }
  }
}
```

---

<a name="quick-start"></a>
## ⚡ Quick Start  

1. Define your servers in `conf-dev.json`.  
2. Copy files to all backend servers:  

```bash
minotaur -c -f ./build/app.tar.gz -t back -e dev
```

3. Connect to all backend servers at once:  

```bash
minotaur -s -t back -e dev
```

---

<a name="contributing"></a>
## 🤝 Contributing  

PRs are welcome! If you’d like to improve Minotaur, fork the repo and submit a pull request.  

---
