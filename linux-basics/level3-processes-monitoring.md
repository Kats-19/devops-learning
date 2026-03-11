# Processes & System Monitoring

---

# 🧠 What Is a Process?

A **process** = a running program.

When you run:

```bash```
ls

A process is created → it runs → it finishes.

Examples:

Opening a browser → process

Running a server → long-running process

Running a script → process

🛠 Step 1 — See Running Processes

Run:

ps

or

ps aux

This shows all running processes.

Columns Meaning
Column	Meaning
USER	Who owns the process
PID	Process ID
%CPU	CPU usage
%MEM	Memory usage
COMMAND	What is running
🔥 Real-Time Monitoring

Run:

top

This shows:

CPU usage

Memory usage

Running processes live

A better interactive version is:

htop

(if installed)

🧪 Step 2 — Create Your Own Process

Run:

sleep 100

Your terminal will freeze for 100 seconds.

Why?

Because sleep is running as a process.

Open another terminal and run:

ps aux | grep sleep

You’ll see your sleep process.

| is called a pipe.

It sends the output of one command into another command.

💀 Killing Processes

Find the PID of the sleep process.

Then run:

kill PID

Replace PID with the actual number.

Your process will stop.

This is how administrators kill stuck applications.

🧠 Background Processes

Run:

sleep 200 &

The & runs the process in the background.

Now run:

jobs

You’ll see the background job.

Bring it back to the foreground:

fg
Services & Logs (Real Server Behavior)

Examples of services:

Web server (nginx)

Database (mysql)

SSH server

Docker daemon

These don't run once — they stay alive continuously.

🧠 What Is a Service?

A service is a background process managed by the system.

On Ubuntu, services are controlled by:

systemctl

This is part of systemd, the system manager.

Step 1 — Check Running Services
systemctl list-units --type=service
🔥 Real DevOps Practice

We will:

Install nginx (a web server)

Start it

Check if it’s running

Inspect logs

🛠 Install Nginx

First update packages:

sudo apt update

Then install nginx:

sudo apt install nginx -y

This is typical production server setup behavior.

🧠 Check If It’s Running
ps aux | grep nginx

If nginx processes appear, it is running.

🌐 Test It

Open your browser and go to:

http://localhost

If nginx started correctly you will see:

Welcome to nginx!

If not, you debug.

That’s DevOps.

📂 Logs — The Most Important Skill

Logs are stored in:

/var/log/

Check nginx logs:

ls /var/log/nginx

You should see:

access.log

error.log

View Logs
cat /var/log/nginx/access.log

Better for real-time monitoring:

tail -f /var/log/nginx/access.log

tail -f shows logs live as they update.

Open localhost again in your browser.

Watch the logs update.

Exit with:

Ctrl + C
🧠 Why Logs Matter

In a real job:

Website down → check /var/log/nginx/error.log

App failing → check logs

Service won't start → logs tell you why

Logs = the truth about what the system is doing.

Example Log Entry
::1 - - [11/Mar/2026:11:16:00 +0100] "GET / HTTP/1.1" 200 409 "-" "Mozilla/5.0 ..."
::1 - - [11/Mar/2026:11:16:01 +0100] "GET /favicon.ico HTTP/1.1" 404 196 "http://localhost/" "Mozilla/5.0 ..."
What It Means

1️⃣ ::1 → IPv6 localhost (similar to 127.0.0.1)

2️⃣ [11/Mar/2026:11:16:00 +0100] → timestamp of the request

3️⃣ "GET / HTTP/1.1" → HTTP method + URL + protocol

4️⃣ 200 → HTTP status code → success

5️⃣ 409 → size of response in bytes

6️⃣ "-" → referrer (none here)

7️⃣ "Mozilla/5.0 ..." → browser user-agent

Second line:

GET /favicon.ico

The browser tried to fetch a favicon.

404

File not found (normal if none exists).

DevOps Insight

You have now:

Installed a real web server

Served requests

Observed live logs

Practiced monitoring processes

This is exactly how production servers are monitored.
