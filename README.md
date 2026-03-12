# penetration-testing-lab
 Web Security & Phishing Awareness Lab | Apache2, SSL, DVWA, Social Engineering Demos
# 🔐 Penetration Testing — Assignment 1
### Web Security & Phishing Awareness Lab

<p align="center">
  <img src="https://img.shields.io/badge/University-AIR%20University%20Islamabad-blue?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Department-Cyber%20Security-red?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Platform-Kali%20Linux-purple?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Status-Completed-green?style=for-the-badge"/>
</p>

---

## 👩‍💻 Student Information

| Field | Details |
|-------|---------|
| **Student Name** | Uliya Fatima |
| **Student ID** | 232098 |
| **University** | AIR University Islamabad |
| **Department** | Cyber Security |
| **Subject** | Web Security / Ethical Hacking |
| **Assignment** | Assignment 1 |
| **Date** | March 2026 |
| **Platform** | Kali Linux (VMware) |

---

## 📋 Assignment Overview

This assignment demonstrates the setup of a secure web server on Kali Linux with a self-signed SSL certificate. The purpose is to understand how phishing attacks work in a **controlled local lab environment**.

> ⚠️ **Disclaimer:** All demonstrations were performed on a **local machine only**. No real users were targeted and no data was collected externally. This is purely for **educational purposes**.

---

## 🎯 Objectives

- ✅ Install and configure Apache2 web server on Kali Linux
- ✅ Create and configure a Self-Signed SSL Certificate using OpenSSL
- ✅ Host a secure HTTPS website locally
- ✅ Install and configure DVWA (Damn Vulnerable Web Application)
- ✅ Demonstrate phishing attack mechanisms through fake social media pages
- ✅ Understand Social Engineering techniques

---

## 🛠️ Tools & Technologies Used

| Tool | Purpose |
|------|---------|
| **Kali Linux** | Operating System (VMware) |
| **Apache2** | Web Server |
| **OpenSSL** | Self-Signed SSL Certificate |
| **DVWA** | Vulnerable Web App for Practice |
| **MariaDB** | Database for DVWA |
| **HTML / CSS** | Custom Phishing Demo Pages |
| **Bash / Terminal** | Command Line Operations |

---

## 📁 Project Structure

```
penetration-testing-232098-uliyaa/
│
├── README.md                        # This file
│
├── Section1_WebServer/
│   ├── apache_install.png           # Apache2 installation screenshot
│   ├── apache_running.png           # Apache2 running status
│   ├── ssl_module.png               # SSL module enabled
│   ├── certificate_creation.png     # Self-signed cert creation
│   └── https_verified.png          # HTTPS verified in browser
│
├── Section2_DVWA/
│   ├── network_config.png           # IP address and network info
│   ├── dvwa_install.png             # DVWA installation
│   ├── dvwa_login.png               # DVWA login page
│   └── dvwa_dashboard.png          # DVWA vulnerability modules
│
├── Section3_MainPage/
│   ├── index.html                   # Main landing page
│   └── main_page_live.png          # Main page in browser
│
├── Section4_Facebook/
│   ├── facebook/index.html          # Fake Facebook login page
│   ├── facebook_login.png           # Facebook page screenshot
│   └── facebook_feed.png           # Fake Facebook home feed
│
├── Section5_YouTube/
│   ├── youtube/index.html           # Fake YouTube page
│   ├── youtube_page.png             # YouTube page screenshot
│   ├── gmail_popup.png              # Gmail popup triggered
│   └── gmail_password.png          # Gmail password step
│
├── Section6_Instagram/
│   ├── instagram/index.html         # Fake Instagram login page
│   ├── instagram_login.png          # Instagram page screenshot
│   └── instagram_feed.png          # Fake Instagram home feed
│
└── Section7_CredentialHarvesting/
    └── screenshots/                 # Toolkit demonstration screenshots
```

---

## 🔧 Section 1: Web Server Setup

### Apache2 Installation
Apache2 web server was installed on Kali Linux using the apt package manager. It hosts web pages locally on **port 80 (HTTP)** and **port 443 (HTTPS)**.

```bash
sudo apt update
sudo apt install apache2 -y
sudo systemctl start apache2
sudo systemctl enable apache2
sudo systemctl status apache2
```

### SSL Module & Self-Signed Certificate
SSL module was enabled and a self-signed certificate was generated using OpenSSL.

```bash
# Enable SSL module
sudo a2enmod ssl

# Create Self-Signed Certificate
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
  -keyout /etc/ssl/private/mysite.key \
  -out /etc/ssl/certs/mysite.crt
```

**Certificate Details:**
- Country: PK
- Organization: AIR UNIVERSITY
- Common Name: LIYAA
- Validity: 365 days
- Encryption: RSA 2048-bit

**SSL Verification Result:**
- ✅ Verified by: AIR UNIVERSITY
- ✅ Connection: Encrypted (TLS 1.3)
- ✅ Cipher: TLS_AES_128_GCM_SHA256

---

## 🌐 Section 2: Network & DVWA Setup

### Network Configuration
```bash
ip a
# Result: eth0 → 192.168.17.128
```

### DVWA Installation
```bash
sudo apt install dvwa -y
sudo ln -s /usr/share/dvwa /var/www/html/dvwa
sudo systemctl start dvwa
sudo systemctl start mariadb
sudo systemctl restart apache2
```

**Access:** `https://localhost/dvwa`  
**Credentials:** admin / password

### DVWA Vulnerability Modules Available
- Brute Force
- Command Injection
- CSRF
- File Inclusion
- SQL Injection
- XSS (Reflected & Stored)
- And more...

---

## 🏠 Section 3: Main Web Page

Custom dark-themed landing page created at `/var/www/html/index.html`

**Features:**
- Matrix rain canvas animation
- Glitch effect on title
- TLS/HTTPS status display
- Links to all demo pages
- AIR University branding

**Access:** `https://localhost`

---

## 📘 Section 4: Facebook Phishing Demo

Fake Facebook login page created to demonstrate social engineering.

```bash
sudo mkdir /var/www/html/facebook
sudo nano /var/www/html/facebook/index.html
```

**Features:**
- Identical Facebook UI design
- Facebook blue color scheme (#1877f2)
- After login → redirects to fake home feed
- Stories, posts, contacts sidebar

**Access:** `https://localhost/facebook`

---

## 📺 Section 5: YouTube Phishing Demo

Fake YouTube page with Gmail credential popup.

```bash
sudo mkdir /var/www/html/youtube
sudo nano /var/www/html/youtube/index.html
```

**Features:**
- Full YouTube UI with video player
- Sidebar with recommendations
- ANY click triggers Gmail Sign-in popup
- Gmail popup: Step 1 (email) → Step 2 (password with avatar)

**Access:** `https://localhost/youtube`

---

## 📸 Section 6: Instagram Phishing Demo *(Bonus)*

Fake Instagram login page as bonus task.

```bash
sudo mkdir /var/www/html/instagram
sudo nano /var/www/html/instagram/index.html
```

**Features:**
- Identical Instagram UI
- Phone mockup on login page
- After login → fake home feed with stories and posts

**Access:** `https://localhost/instagram`

---

## 🎣 Section 7: Credential Harvesting

Demonstration of credential harvesting toolkit in a controlled lab environment.

> ⚠️ **Note:** This was performed entirely on local machine for educational demonstration only.

---

## 📚 Key Concepts Learned

1. **Web Server Configuration** — Apache2 setup, virtual hosts, port configuration
2. **SSL/TLS** — Certificate creation, HTTPS setup, encryption verification
3. **Social Engineering** — How phishing pages mimic legitimate websites
4. **DVWA** — Practice environment for web vulnerabilities
5. **Phishing Awareness** — Understanding attack vectors to better defend against them

---

## ⚠️ Ethical Notice

```
This project was created ONLY for educational purposes as part of 
AIR University Cyber Security curriculum.

❌ Do NOT use these techniques on real websites or real people
❌ Do NOT deploy these pages on public servers  
❌ Do NOT collect real credentials

✅ All tests performed on LOCAL machine only (VMware/Kali Linux)
✅ No real users were targeted
✅ No data was collected or transmitted externally
```

---

## 📞 Contact

**Uliya Fatima** — AIR University Islamabad  
📧 uliyafatima82@gmail.com  
🎓 Student ID: 232098 | Cyber Security Department

---

<p align="center">
Made with 💻 for AIR University Cyber Security Assignment 1 | March 2026
</p>
