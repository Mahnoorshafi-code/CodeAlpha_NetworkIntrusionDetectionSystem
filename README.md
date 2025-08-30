🚨 Network Intrusion Detection with Suricata
📌 Project Overview

This project demonstrates the use of Suricata as a Network Intrusion Detection System (NIDS) on Kali Linux.
We created a custom detection rule to identify ICMP (ping) traffic, generated ping requests, and verified that Suricata successfully logged alerts.

⚙️ Installation
Step 1: Update system
sudo apt update && sudo apt upgrade -y

Step 2: Install Suricata
sudo apt install suricata -y

🛠️ Configuration
Edit Suricata config file
sudo nano /etc/suricata/suricata.yaml


Update default rule path:

default-rule-path: /etc/suricata/rules


Ensure the rules section includes:

rule-files:
  - local.rules

✍️ Create Custom Rule

Open the local rules file:

sudo nano /etc/suricata/rules/local.rules


Add this ICMP detection rule:

alert icmp any any -> any any (msg:"ICMP Ping detected"; sid:1000001; rev:1;)

🚀 Running Suricata
Test configuration
sudo suricata -T -c /etc/suricata/suricata.yaml

Start IDS mode
sudo suricata -c /etc/suricata/suricata.yaml -i eth0 -v

🔍 Testing the Rule

Generate ping traffic:

ping -c 4 8.8.8.8


Check alerts:

sudo tail -f /var/log/suricata/fast.log


✅ Expected output:

[**] [1:1000001:1] ICMP Ping detected [**]

📸 Screenshots

Insert your screenshots here:

Suricata installation

local.rules with custom rule

Config test success

Ping test results

fast.log alerts

🏁 Conclusion

We successfully configured Suricata to detect ICMP ping traffic.
This project shows how Suricata can be customized with rules to detect suspicious activities such as scans, DoS attacks, and malicious payloads.
