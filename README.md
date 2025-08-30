# 🛡 Network Intrusion Detection System (NIDS) with Suricata  

## 📌 Project Overview
This project implements a *Network Intrusion Detection System (NIDS)* using *Suricata*.  
It monitors network traffic in real-time, applies detection rules, and generates alerts for suspicious activity.  
As a demo, we configure Suricata to detect *ICMP Ping traffic*.  

---

## 🚀 Features
- Rule-based intrusion detection  
- Real-time packet inspection  
- Custom rule for ICMP ping detection  
- Logging and alert generation  
- Works with Linux systems  

---

## 🛠 Installation  

Update and install Suricata:  

```sudo apt update && sudo apt upgrade -y
```sudo apt install suricata -y

##  Configuration

sudo nano /etc/suricata/suricata.yaml
default-rule-path: /etc/suricata/rules rule-files: - local.rules 

## Add Custom Detection Rule

sudo nano /etc/suricata/rules/local.rules

alert icmp any any -> any any (msg:"ICMP Ping detected"; sid:1000001; rev:1;) 

## Test the Configuration

sudo suricata -T -c /etc/suricata/suricata.yaml 

## ▶ Running Suricata

sudo suricata -c /etc/suricata/suricata.yaml -i eth0 

## 🧪 Generating Test Traffic

ping -c 4 8.8.8.8 

## 📄 Viewing Alerts

cat /var/log/suricata/fast.log 

## Example Output:

08/30/2025-14:21:12.345678 [] [1:1000001:1] ICMP Ping detected [] [Classification: Misc activity] [Priority: 3] {ICMP} 192.168.1.10 -> 8.8.8.8 


## 🔍 Technical Details

Tool: Suricata IDS

OS: Linux (tested on Ubuntu/Debian)

Protocols Monitored: ICMP, TCP, UDP, HTTP

Log Files: /var/log/suricata/fast.log, /var/log/suricata/eve.json

## 📜 License

This project is licensed under the MIT License.
