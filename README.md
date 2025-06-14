🚀 GitHub SSH Guide: Upload and Download Files

This guide shows you how to:

✅ Set up SSH with GitHub

🧾 Set your Git name and email

⬆️ Upload (push) files to GitHub

⬇️ Download (clone) files from GitHub



---

🛠️ 1. Set Up SSH (Do Once)

🔐 1.1 – Make a New SSH Key

ssh-keygen -t ed25519 -C "your_email@example.com"

Press Enter to save in the default location

Press Enter again for no passphrase (or type one for extra security)


⚙️ 1.2 – Start the SSH Agent

eval "$(ssh-agent -s)"

➕ 1.3 – Add Your SSH Key to the Agent

ssh-add ~/.ssh/id_ed25519

📋 1.4 – Copy Your SSH Key

cat ~/.ssh/id_ed25519.pub

Copy the full key (starts with ssh-ed25519)


🔗 1.5 – Add the Key to GitHub

Open GitHub SSH settings

Click New SSH key

Paste your key, give it a name, and save


✅ 1.6 – Test If SSH Works

ssh -T git@github.com

You should see:


Hi username! You've successfully authenticated, but GitHub does not provide shell access.


---

🧾 2. Set Git Name and Email (Do Once)

👤 Configure Your Identity

git config --global user.name "Your Name"
git config --global user.email "your@email.com"

🔍 Check Current Settings

git config --global user.name
git config --global user.email

🔒 Optional: Mark Folder as Safe (Avoid Warnings)

git config --global --add safe.directory ...


---

⬆️ 3. Upload Files to GitHub Using SSH

🌿 3.1 – Set main as Default Branch (Do Once)

git config --global init.defaultBranch main

🆕 3.2 – Make a New GitHub Repo

Go to Create New Repo

Name your repo

Uncheck “Initialize with README”

Click Create repository


📁 3.3 – Create Local Folder and Git Repo

mkdir my-repo
cd my-repo
git init

📄 3.4 – Add a File and Commit

echo "Hello GitHub" > file.txt
git add file.txt
git commit -m "Initial commit"

🔗 3.5 – Connect to GitHub and Upload

git remote add origin git@github.com:your-username/my-repo.git
git branch -M main
git push -u origin main


---

⬇️ 4. Download a GitHub Repo Using SSH

📎 4.1 – Copy SSH Link from GitHub

Go to your repo → Code → SSH

Copy the SSH link


📥 4.2 – Clone It

git clone git@github.com:your-username/my-repo.git


---

> 🎉 All done! You can now securely push and pull code with GitHub using SSH.



