# 🔹 Task 1 — Verify System Network Identity

### 1️⃣ Check IP Address
```bash
ipaddr
iproute
hostname -I

My IP Address: 172.25.155.54
Network Interface: eth0
```
<img width="1919" height="601" alt="image" src="https://github.com/user-attachments/assets/755f707f-4c9a-40ba-9762-63015afce129" />


# 🔹 Task 2 — Test Internet Connectivity Flow

### 3️⃣ Test Connectivity

```bash

1.Check connectivity by IP:
ping 8.8.8.8 1

2.Check DNS resolution:
ping google.com 1

3.Trace the route:
traceroute google.com
```
<img width="1919" height="469" alt="image" src="https://github.com/user-attachments/assets/136e81f8-9a50-4949-80ab-d811d2b25c3e" />

<img width="1919" height="302" alt="image" src="https://github.com/user-attachments/assets/e7668e72-b58c-4e64-8eee-abab7496a513" />



# 🔹 Task 3 — Analyze DNS in Detail

```bash
dig google.com

<img width="1919" height="465" alt="image" src="https://github.com/user-attachments/assets/87675ffa-4f48-4da7-aa82-b53c912da99b" />

 dig abcxyz12345testdomain.com

<img width="1914" height="480" alt="image" src="https://github.com/user-attachments/assets/91efc76e-3f68-433c-a936-ebb933b857ba" />

 nslookup google.com
```
<img width="1919" height="229" alt="image" src="https://github.com/user-attachments/assets/215689ae-fbe8-4403-90cd-d20601845d0c" />


# 🔹 Task 4 — Host a Simple Website Locally

```bash

Install Nginx

<img width="1915" height="61" alt="image" src="https://github.com/user-attachments/assets/0d8b7261-85a6-488a-aed5-8622ccdcdaf2" />

echo "Hello from my server - Dhanashree DevOps Lab" | sudo tee /var/www/html/index.html

curl http://localhost
```
<img width="1918" height="1042" alt="day_3_task_4" src="https://github.com/user-attachments/assets/2354fdd8-cd59-42d6-8cca-b845f1446a1c" />
```
curl -I http://localhost
```
<img width="1919" height="356" alt="image" src="https://github.com/user-attachments/assets/5fbb1c11-99a7-4468-947d-0f8fae90f81f" />


# 🔹 Task 5 — Check Listening Ports

```bash
sudo systemctl stop nginx

ss -tuln | grep 80
```
<img width="1919" height="53" alt="image" src="https://github.com/user-attachments/assets/0e1de6fb-44d3-4fb4-942a-51d2c5475630" />


# 🔹 Task 6 — Test Application Connectivity

```bash

Fetch HTTP headers:

  curl -I http://localhost

Observe status code and server response.
```
<img width="1918" height="388" alt="image" src="https://github.com/user-attachments/assets/87722d99-d7b9-453c-afe8-adb22e228915" />
```
Download content:
  wget http://localhost
```
<img width="1919" height="255" alt="image" src="https://github.com/user-attachments/assets/70e449de-871a-41fc-a1b7-e0c53511193b" />


# 🔹 Task 7 — Simulate a Firewall Restriction (UFW)

```bash
Enable Firewall
sudo ufw enable

Default Policy:

Deny incoming

Allow outgoing

Allow Web Traffic
sudo ufw allow 80
sudo ufw allow 443
Deny SSH
sudo ufw deny 22

✔ SSH blocked
✔ Web still accessible

sudo ufw status
```
<img width="1918" height="945" alt="image" src="https://github.com/user-attachments/assets/f9f946e5-f46b-49a4-876c-52886495b952" />

# 🔹 Task 8 — Create a Local Domain Using /etc/hosts

```bash
Edit /etc/hosts
sudo vi /etc/hosts

Add:

127.0.0.1 mytest.local
Test Domain
ping mytest.local -c 1
curl http://mytest.local

✔ Resolved to 127.0.0.1
✔ Website loaded successfully
```
<img width="1919" height="532" alt="image" src="https://github.com/user-attachments/assets/0f6a91c9-bdd5-425f-9d23-a9d931c93f5c" />









