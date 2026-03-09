# Terminal Foundations

## 🧠 Step 1 — Understand Where You Are

`pwd` → gives the current directory

Linux has a **tree structure**.

### Important folders

| Folder | Meaning |
|------|------|
| `/` | Root of everything |
| `/home` | User folders |
| `/etc` | Configuration files |
| `/var` | Logs & variable data |
| `/bin` | Essential commands |
| `/usr` | Installed programs |

---

## 🛠 Step 2 — Navigation Mastery

Important shortcuts:

- `~` → your home directory
- `..` → one level up
- `.` → current directory

---

## 🏗 Step 3 — Create Your DevOps Lab

Inside your home directory:

```bash```
mkdir devops_lab
cd devops_lab

Create structure:
```bash```
mkdir logs scripts configs
touch app.py
touch logs/server.log
touch configs/app.conf

Now view everything:
```bash```
ls -R

### Mini Production structure
devops_lab/
├── app.py
├── logs/
  └── server.log
├── configs/
  └── app.conf
└── scripts/

This is how servers are organized

## 📖Step 4 - Reading and Writing Files
Write something:
```bash```
echo "Server started" > logs/server.log

Append something:
```bash```
echo "Error at 10:00" >> logs/server.log

Now read it:
```bash```
cat logs/server.log

Better way (for big files):
```bash```
less logs/server.log

In production
Something breaks
You check logs
You debug

---

