# DevOps Linux Basics

---

# 1️⃣ Package Managers (`apt`)

Linux installs software using **package managers**.

On Ubuntu we use:

```bash```
apt

Instead of downloading .exe files like on Windows.

Update Package List
sudo apt update

This refreshes the list of available software.

Upgrade Installed Packages
sudo apt upgrade

Updates software already installed on the system.

Install Software

Example:

sudo apt install tree

Now run:

tree

It prints folder structures nicely.

Try inside your DevOps lab:

tree ~/devops_lab
Remove Software
sudo apt remove tree

💡 DevOps engineers constantly install tools like:

docker

nginx

git

node

python

monitoring tools

Understanding package managers is essential.

# 2️⃣ Environment Variables

Environment variables store system configuration values.

Example:

echo $HOME

Output:

/home/keni

Another example:

echo $PATH

PATH tells Linux where to look for commands.

Example directories:

/usr/bin
/usr/local/bin
/bin

When you run:

ls

Linux searches those directories to find the command.

Create Your Own Variable
export PROJECT="devops_lab"

Check it:

echo $PROJECT

Output:

devops_lab
# 3️⃣ Git in Linux

Most DevOps work happens with Git repositories.

Check if Git is installed:

git --version

If not installed:

sudo apt install git
Initialize a Repository

Inside your DevOps lab:

cd ~/devops_lab
git init

Now Git is tracking the folder.

Add Files
git add .

Commit changes:

git commit -m "Initial commit"

Git + Linux + automation = core DevOps workflow.

# 4️⃣ Docker Basics (Concept)

Docker runs applications inside containers.

Think of containers as isolated mini-computers.

Example container stack:

server
 ├ nginx container
 ├ app container
 └ database container

Every DevOps engineer uses Docker.

We won’t install it in WSL yet, but understanding the concept is important.

# 5️⃣ Deployment Simulation (Important)

Let’s simulate deploying an application.

Inside your DevOps lab:

mkdir deployment
cd deployment

Create a fake app:

echo "Hello from my server" > index.html

Copy it to the nginx directory:

sudo cp index.html /var/www/html/index.html

Now open in your browser:

http://localhost

Your text should appear.

You just simulated a deployment.

This is literally what happens when applications go live.
