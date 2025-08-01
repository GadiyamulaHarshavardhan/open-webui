# open-webui dev instructions

Great! Since you're starting **fresh on a new system**, I'll walk you through **each step** to set up Open WebUI from scratch. This includes installing required frameworks and tools for both frontend and backend development. Here's your **clean and clear step-by-step setup guide**:

---

# ✅ **Full Local Setup Guide for Open WebUI (From Scratch)**

---

## 🧰 **1. Prerequisites – Tools to Install First**

Make sure your system has the following:

| Requirement | Version                  | How to Install                              |
| ----------- | ------------------------ | ------------------------------------------- |
| OS          | Linux (Ubuntu preferred) | You're already using Pop!\_OS ✅             |
| Python      | 3.11+                    | We’ll install via Miniconda (recommended)   |
| Node.js     | 22.10+                   | Will install via Node Version Manager (nvm) |
| Git         | Latest                   | Used for cloning repos                      |
| IDE         | VS Code                  | Recommended for terminal and editing        |

---

### 🔧 1.1. Install Git

```bash
sudo apt update
sudo apt install git -y
```

---

### 🔧 1.2. Install Miniconda (to manage Python easily)

```bash
cd ~
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
```

* Press `Enter` multiple times.
* Accept license with `yes`.
* Choose install path (default is fine).
* Once done:

```bash
source ~/.bashrc
```
command to deactivate conda in terimal perimentaly:
'''bash
conda config --set auto_activate_base False
'''
---

### 🔧 1.3. Install Node.js (via nvm)

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
source ~/.bashrc
nvm install 22.10
nvm use 22.10
```

Check:

```bash
node -v
npm -v
```

---

### 🔧 1.4. Install VS Code (if not installed)

```bash
sudo apt install software-properties-common apt-transport-https wget -y
wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
sudo apt update
sudo apt install code
```

---

## 🧱 **2. Clone Open WebUI Repository**

```bash
cd ~
git clone https://github.com/open-webui/open-webui.git
cd open-webui
```

---

## 🌐 **3. Frontend Setup (React + Vite)**

### 📂 3.1. Copy `.env` File

```bash
cp -RPp .env.example .env
```

You can edit `.env` later if needed:

```bash
code .env
```

---

### 📦 3.2. Install Frontend Dependencies

```bash
npm install
```

---

### 🚀 3.3. Start Frontend Server

```bash
npm run dev
```

Visit in browser:

```
http://localhost:5173
```

---

## 🧠 **4. Backend Setup (Python API with FastAPI)**

### 🗂 4.1. Open New Terminal in VS Code

In **VS Code**:

* Terminal → New Terminal
* Or use shortcut: `Ctrl + Shift + `

---

### 🐍 4.2. Create and Activate Conda Environment

```bash
cd ~/open-webui/backend
conda create --name open-webui python=3.11 -y
conda activate open-webui
```

---

### 📦 4.3. Install Python Dependencies

```bash
pip install -r requirements.txt -U
```

---

### 🚀 4.4. Start Backend Server

```bash
sh dev.sh
```

If the backend runs successfully, visit:

```
http://localhost:8080/docs
```

---

## 🌐 **5. View Full App in Browser**

Go back to:

```
http://localhost:5173
```

You’ll now see the full working UI, connected to your local backend 🎉

---

## 🧹 **6. Fix Common Issues**

### ❗ "Address already in use"

To find what's using the port:

```bash
sudo lsof -i :5173
sudo lsof -i :8080
```

To kill the process:

```bash
kill -9 <PID>
```

---

### 🧠 "Heap Memory Error (Frontend)"

If build crashes with memory error:

```bash
export NODE_OPTIONS="--max-old-space-size=4096"
npm run dev
```

Use this every time before starting `npm run dev`.

---

## 🤝 **7. Contribute to Open WebUI**

### 🔄 7.1. Create a Feature Branch

```bash
git checkout dev
git pull origin dev
git checkout -b my-feature-branch
```

### ✅ 7.2. Commit Clearly

```bash
git add .
git commit -m "Fix: Updated login styling"
```

### 🔃 7.3. Push and Create PR

```bash
git push origin my-feature-branch
```

Then go to GitHub → open a **Pull Request** into `dev` branch.

---

## 🎯 Summary of Commands

```bash
# Install tools
sudo apt install git -y
bash Miniconda3-latest-Linux-x86_64.sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash

# Clone and setup
git clone https://github.com/open-webui/open-webui.git
cd open-webui
cp -RPp .env.example .env
npm install
npm run dev   # frontend

# Backend in new terminal
cd backend
conda create --name open-webui python=3.11 -y
conda activate open-webui
pip install -r requirements.txt -U
sh dev.sh     # backend
```

---

Would you like me to:

* ✅ Help you **install all tools now** (copy-paste ready for your Pop!\_OS)?
* ✅ Show how to **change ports**, **connect Postgres**, or **enable Docker**?
* ✅ Prepare a `.sh` setup script to automate everything?

Let me know your next step!
