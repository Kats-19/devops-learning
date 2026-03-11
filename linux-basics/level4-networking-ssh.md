#DevOps Linux Training — Level 4
#🌐 Networking & Remote Access

Networking is a core DevOps skill because servers communicate with each other through the network.

At this level you will learn:

Ports

Checking open services

Testing connectivity

Testing web servers from the terminal

Remote server access with SSH

#🌐 Step 1 — Understanding Ports

Think of a server like a hotel.

Concept	Example
IP Address	Hotel address
Port	Room number
Service	Person in the room

Example connections:

localhost:80 → Web server (HTTP)

server_ip:22 → SSH remote terminal

server_ip:443 → HTTPS secure web traffic

Common ports:

Port	Service
22	SSH
80	HTTP
443	HTTPS
3306	MySQL
5432	PostgreSQL
🔍 Checking Open Ports

To see which services are listening on your machine:

sudo ss -tuln

Explanation:

Flag	Meaning
ss	socket statistics
t	TCP connections
u	UDP connections
l	listening services
n	numeric output

Example output:

LISTEN 0      128       0.0.0.0:22        0.0.0.0:*
LISTEN 0      128       127.0.0.1:80      0.0.0.0:*

Meaning:

Port 22 → SSH server listening

Port 80 → HTTP server (nginx)

This command is commonly used in server debugging.

#🛠 Step 2 — Ping

ping checks whether a host is reachable.

ping -c 4 google.com

Explanation:

Option	Meaning
-c 4	send 4 packets

Example output:

0% packet loss
time=17 ms

Meaning:

The server is reachable

Network connectivity is working

Latency (~17ms) is normal

DevOps engineers use ping to quickly test:

internet connectivity

server availability

network latency

#🛠 Step 3 — Curl (Testing Web Services)

curl allows you to test web servers directly from the terminal.

Example:

curl http://localhost

If nginx is running, you will see the HTML of the default nginx page.

Checking HTTP Headers
curl -I http://localhost

Explanation:

Option	Meaning
-I	show response headers only

Example output:

HTTP/1.1 200 OK
Server: nginx/1.24.0

Meaning:

HTTP status 200 OK

nginx successfully responded

This command is extremely useful for debugging APIs and web services.

#🛠 Step 4 — SSH (Remote Server Access)

SSH stands for Secure Shell.

It allows you to remotely log into servers.

Basic syntax:

ssh username@server_ip

Example:

ssh keni@localhost

First connection steps:

Accept the server fingerprint

Enter your password

Once connected, you will have remote terminal access.

This is how DevOps engineers manage:

cloud servers

production systems

remote infrastructure

#⚠️ SSH in WSL

If you see this error:

ssh: connect to host localhost port 22: Connection refused

This means:

The SSH server is not running

This is normal in WSL.

To install it:

sudo apt install openssh-server

Then start it with:

sudo service ssh start
