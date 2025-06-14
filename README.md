# GitHub SSH Guide: Upload and Download Files

This guide shows you how to:

* ✅ Set up SSH with GitHub
* ✍️ Set your Git name and email
* ⬆️ Upload (push) files to GitHub
* ⬇️ Download (clone) files from GitHub

---

## 🛠️ 1. Set Up SSH (Do Once)

### 1.1 – Make a New SSH Key

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

* Press **Enter** to save in the default place
* Press **Enter** again when asked for passphrase (or type one to protect your key)

### 1.2 – Start the SSH Agent

```bash
eval "$(ssh-agent -s)"
```

### 1.3 – Add Your SSH Key to the Agent

```bash
ssh-add ~/.ssh/id_ed25519
```

### 1.4 – Copy Your SSH Key

```bash
cat ~/.ssh/id_ed25519.pub
```

* Copy the full key (starts with `ssh-ed25519`)

### 1.5 – Add the Key to GitHub

* Go to [GitHub SSH settings](https://github.com/settings/keys)
* Click **New SSH key**
* Paste your key and save it

### 1.6 – Test If SSH Works

```bash
ssh -T git@github.com
```

---

## 🧾 2. Set Git Name and Email (Do Once)

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

To check:

```bash
git config --global user.name
git config --global user.email
```

---

## ⬆️ 3. Upload Files to GitHub Using SSH

### 3.1 – Set `main` as Default Branch (Do Once)

```bash
git config --global init.defaultBranch main
```

### 3.2 – Make a New GitHub Repo

* Go to [https://github.com/new](https://github.com/new)
* Give it a name, uncheck **README**, and create it

### 3.3 – Create Local Folder and Git Repo

```bash
mkdir my-repo
cd my-repo
git init
```

### 3.4 – Add a File and Save It

```bash
echo "Hello GitHub" > file.txt
git add file.txt
git commit -m "Initial commit"
```

### 3.5 – Connect to GitHub and Upload

```bash
git remote add origin git@github.com:your-username/my-repo.git
git branch -M main
git push -u origin main
```

---

## ⬇️ 4. Download a GitHub Repo Using SSH

### 4.1 – Copy SSH Link from GitHub

* Click **Code** → **SSH** and copy it

### 4.2 – Clone It

```bash
git clone git@github.com:your-username/my-repo.git
```

---

> ✅ Done! You’re all set to use Git and GitHub with SSH.
