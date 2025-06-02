# GitHub SSH Guide: Upload and Download Files

This guide shows you how to:

* ✅ Set up SSH with GitHub
* ⬆️ Upload (push) files to GitHub
* ⬇️ Download (clone) files from GitHub

---

## 🛠️ 1. Set Up SSH (Do Once)

### 1.1 – Make a New SSH Key

In your terminal, type:

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

* Press **Enter** to save in the default place
* Press **Enter** again when asked for passphrase (or type one to protect your key)

### 1.2 – Start the SSH Agent

```bash
eval "$(ssh-agent -s)"
```

* This helps your computer remember the SSH key

### 1.3 – Add Your SSH Key to the Agent

```bash
ssh-add ~/.ssh/id_ed25519
```

### 1.4 – Copy Your SSH Key

```bash
cat ~/.ssh/id_ed25519.pub
```

* Select and copy the whole output (it starts with `ssh-ed25519`)

### 1.5 – Add the Key to GitHub

* Go to [GitHub SSH settings](https://github.com/settings/keys)
* Click **New SSH key**
* Paste the copied key
* Give it a name (like "My Laptop") and save it

### 1.6 – Test If SSH Works

```bash
ssh -T git@github.com
```

* If asked, type `yes`
* You should see a message like:

```
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

---

## ⬆️ 2. Upload Files to GitHub Using SSH

### 2.1 – Set `main` as Default Branch (Do Once)

```bash
git config --global init.defaultBranch main
```

* Makes sure your first branch is always called `main`

### 2.2 – Make a New GitHub Repo

* Go to [https://github.com/new](https://github.com/new)
* Give it a name
* **Do not** check "Initialize with README"
* Click **Create repository**

### 2.3 – Create Local Folder and Git Repo

```bash
mkdir my-repo
cd my-repo
git init
```

* This makes a folder and starts git inside it

### 2.4 – Add a File and Save It

```bash
echo "Hello GitHub" > file.txt
git add file.txt
git commit -m "Initial commit"
```

### 2.5 – Connect to GitHub and Upload

Copy the SSH link from your GitHub repo. Then:

```bash
git remote add origin git@github.com:your-username/my-repo.git
git branch -M main
git push -u origin main
```

* This links your local folder to GitHub and uploads the code

---

## ⬇️ 3. Download a GitHub Repo Using SSH

### 3.1 – Copy SSH Link from GitHub

* Go to the repo page
* Click **Code** button
* Choose **SSH** and copy the link (e.g., `git@github.com:your-username/my-repo.git`)

### 3.2 – Clone It to Your Computer

```bash
git clone git@github.com:your-username/my-repo.git
```

* This downloads the code into a folder

---

> ✅ That’s it! You can now push and pull code from GitHub using SSH. It’s faster and safer than using passwords.
