# 🛡️ Real-Time Threat Detection using Snort IDS on Ubuntu

A lightweight yet powerful IDS setup using **Snort 2.x** on Ubuntu to detect common network threats such as **ICMP scans**, **SSH brute-force attempts**, and **HTTP traffic anomalies**.  
This is part of my hands-on **SOC Analyst** learning journey to build real-world detection capabilities.

---

## ⚙️ Tools & Environment

- 🐧 Ubuntu 20.04 / 22.04 (Target System)  
- 🧠 Snort 2.x (Intrusion Detection System)  
- 🕸️ Apache2 Web Server  
- 🔐 OpenSSH Server  
- 💻 Kali Linux (Attacker Simulation)

---

## 🚨 Custom Detection Rules (Snort)

```snort
alert icmp any any -> $HOME_NET any (msg:"ICMP Packet Monitor"; sid:100786; rev:1;)
alert tcp any any -> $HOME_NET 22 (msg:"SSH Brute Force Attempt"; sid:107806; rev:1;)
alert tcp any any -> $HOME_NET 80 (msg:"HTTP Alert - Port 80 Access"; sid:708603; rev:1;)
```

📁 Save these rules in:  
`/etc/snort/rules/local.rules`

---

## 🧪 Threat Simulation Commands

On Kali or attacker VM:

```bash
# ICMP Ping (Recon)
ping <Ubuntu-IP>

# SSH Brute Force (Manual or via Hydra)
ssh test@<Ubuntu-IP>

# HTTP Request
curl http://<Ubuntu-IP>
```

---

## ▶️ Run Snort in Console Mode

```bash
sudo snort -A console -q -c /etc/snort/snort.conf -i eth0
```

> Make sure your interface (e.g., eth0, ens33) is correct using `ip a`.

---

## 📈 Output

- Alerts appear directly in the terminal console or in log file (`/var/log/snort/alert`)
- Messages match your custom rule descriptions
- Can be forwarded to SIEM tools (e.g., Splunk) for real-time correlation

---

## 🎓 Learning Highlights

- ✅ Wrote custom detection rules in Snort  
- ✅ Simulated ICMP, SSH, and HTTP-based threats  
- ✅ Monitored and validated alerts live  
- ✅ Practiced Blue Team concepts in real environment

---

## 👨‍💻 Author

**Afroz Shaikh**  
📧 afrozshaikh8086@gmail.com  
🎯 SOC Analyst in Training  
🔐 Focus: Threat Detection | Splunk | IDS/IPS | Linux Security | Real-World Projects
