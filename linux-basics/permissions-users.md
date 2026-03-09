# Linux Permissions, Users & Sudo

---

# 🧠 Step 1 — Look at Permissions

## 🧩 Anatomy of Linux Permissions

Example:


-rwxr-xr--


Break it into chunks:


rwxr-xr--
│ │ │ │
│ │ │ └── Others
│ │ └──────── Group
│ └────────────── Owner
└─────────────────── Filetype


---

## 🔹 First Character — File Type

| Symbol | Meaning |
|------|------|
| `-` | Regular file |
| `d` | Directory |
| `l` | Symbolic link |

---

## 🔹 The 9 Permission Characters

They come in groups of 3.

| Position | Meaning |
|------|------|
| 1–3 | Owner permissions |
| 4–6 | Group permissions |
| 7–9 | Others permissions |

Each group contains:

| Letter | Meaning |
|------|------|
| `r` | Read |
| `w` | Write |
| `x` | Execute |

---

### For a FILE

- `r` → can read content  
- `w` → can modify file  
- `x` → can execute it (run it like a program)

---

### For a DIRECTORY

- `r` → can list contents  
- `w` → can create/delete inside it  
- `x` → can enter it (`cd`)

---

# 🛠 Step 2 — Understanding `chmod`

## Method 1 — Symbolic (Beginner Friendly)

```bash```
chmod u+x file
Symbol	Meaning
u	user (owner)
g	group
o	others
a	all
+	add permission
-	remove permission
-	
Examples
chmod u+x script.sh
chmod g-w file.txt
chmod o-r file.txt

Method 2 — Numeric (VERY IMPORTANT for DevOps)

Permissions are numbers.

Permission	Value
r	4
w	2
x	1

Add them together:

Combo	Value
rwx	7
rw-	6
r-x	5
r--	4

Example:

chmod 755 script.sh

Meaning:

Owner  → 7 (rwx)
Group  → 5 (r-x)
Others → 5 (r-x)
🚀 DevOps Reality

When you deploy apps:

Scripts must be executable (chmod +x)

Config files should not be writable by everyone

Logs must have correct ownership

Services fail if permissions are wrong

⚠️ Permission errors are VERY common in real DevOps jobs.

## 🔥 LEVEL 2 — Users, Groups & Sudo
Check your user
whoami
See detailed user info
id

Important parts:

uid → your user ID

gid → your main group

groups → extra groups (sudo group is important)

🧠 What Is root?

Linux has a superuser called:

root

Root can:

Modify system files

Install software

Kill any process

Change any permission

Regular users cannot do these things.

That is Linux security.

🔑 What Is sudo?

sudo means:

Super User Do

It temporarily gives you root privileges.

Example:

sudo apt update

Without sudo you would get:

Permission denied
🚨 DevOps Reality

On production servers:

You do NOT log in as root

You use sudo

You restrict who has sudo access

Security is critical in real infrastructure.

🧠 Ownership

Every file has:

Owner + Group

Example:

keni keni

This means:

Owner → keni

Group → keni

Change ownership
sudo chown keni:keni filename

This changes both the owner and group of a file.
