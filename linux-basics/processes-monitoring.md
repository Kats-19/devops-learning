# Linux Processes & System Monitoring

---

# 🧠 What Is a Process?

A **process** is a running program.

When you run:

```bash```
ls

A process is created.

It runs.

It finishes.

Examples of processes:

Opening a browser → process

Running a server → long-running process

Executing a command → temporary process

## 🛠 Step 1 — See Running Processes

Run:

ps

or

ps aux

This shows all processes running on the system.

Column meanings
Column	Meaning
USER	Who owns the process
PID	Process ID
%CPU	CPU usage
%MEM	Memory usage
COMMAND	What program is running
🔥 Real-Time Monitoring

Run:

top

This provides live system monitoring.

You will see:

CPU usage

Memory usage

Running processes in real time

System load

This command is commonly used when diagnosing performance issues on servers.

## 🧪 Step 2 — Create Your Own Process

Run:

sleep 100

Your terminal will pause for 100 seconds.

Why?

Because the sleep command is running as a process.

Observe the process from another terminal

Open another terminal tab and run:

ps aux | grep sleep

You will see your sleep process running.

What is | ?

| is called a pipe.

It sends the output of one command into another command.

Example:

ps aux → list processes
grep sleep → search for "sleep"
💀 Killing Processes

Find the PID of the sleep process.

Then run:

kill PID

Replace PID with the actual process ID.

Example:

kill 12345

Your process will stop.

This is how system administrators terminate stuck applications.

# 🧠 Background Processes

Run:

sleep 200 &

The & symbol runs the command in the background.

Now check running background jobs:

jobs

You will see the job running.

Bring the job back to the foreground
fg

This resumes the process in the terminal.

# 🚀 DevOps Reality

Process management is critical for DevOps engineers.

Common scenarios:

Killing stuck services

Monitoring CPU and memory usage

Identifying runaway processes

Diagnosing server performance problems

Tools like ps, top, and kill are used daily when managing production systems.


---
