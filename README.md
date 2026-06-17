# 🛡️ Network Security Lab — OPNsense + Suricata

A virtualized network security lab simulating an office environment with OPNsense firewall, Suricata IDS, traffic monitoring, and alias-based rule management.

---

## 📌 Overview

This lab demonstrates core network defense concepts by setting up a controlled environment where an attacker machine (Kali Linux) attempts various attacks against a target (Windows), while OPNsense acts as the perimeter firewall with Suricata IDS providing intrusion detection and prevention.

---

## 🖥️ Lab Architecture

```
+-------------------+       +-------------------+       +-------------------+
|   Kali Linux      |       |    OPNsense        |       |   Windows Target  |
|  (Attacker)       | ----> |    (Firewall)      | ----> |   (Victim)        |
|  10.0.0.73        |       |    10.0.0.2        |       |   10.0.0.62       |
+-------------------+       +-------------------+       +-------------------+
                                    |
                             VMnet10 (Isolated)
```

| Machine        | Role        | IP Address  |
|----------------|-------------|-------------|
| OPNsense       | Firewall    | 10.0.0.2    |
| Kali Linux     | Attacker    | 10.0.0.73   |
| Windows 10     | Target      | 10.0.0.62   |

---

## ✅ Tasks Implemented

### Task 1 — Firewall Rules
- Block all traffic from Kali → Windows
- Block ports 80, 22, 443
- Block ICMP (ping)
- Rules managed via Aliases for dynamic updates

### Task 2 — Suricata IDS/IPS
- Configured on LAN interface in **Netmap IPS mode**
- Enabled **ET Open rulesets**:
  - `emerging-scan`
  - `emerging-dos`
  - `emerging-worm`
  - `emerging-tor`
- Custom rule: **"Kali Linux Traffic Detection"**
- 3 active policies configured

### Task 3 — Traffic Monitoring & Live Logs
- Real-time traffic monitoring via OPNsense dashboard
- Live log analysis of blocked/allowed connections
- Suricata alert logs reviewed for triggered rules

### Task 4 — Aliases
| Alias Name    | Value        | Purpose                   |
|---------------|--------------|---------------------------|
| KaliHost      | 10.0.0.73    | Attacker machine reference|
| BlockedPorts  | 80, 22, 443  | Ports to block            |

---

## 🔥 Bonus — Attack Simulation

| Attack           | Tool    | Result                        |
|------------------|---------|-------------------------------|
| Brute Force SSH  | Hydra   | ✅ Blocked by Suricata IPS drop rule |
| Dynamic Alias Update | Manual | ✅ Rules updated without restart |

---

## 🛠️ Tools & Technologies

- **OPNsense** — Open-source firewall/router
- **Suricata** — IDS/IPS engine
- **Kali Linux** — Penetration testing OS
- **VMware Workstation** — Virtualization (VMnet10)
- **Hydra** — Brute force testing tool
- **ET Open Rulesets** — Community threat intelligence rules

---

## 📚 Concepts Demonstrated

- Firewall rule creation and ordering
- Intrusion Detection vs Intrusion Prevention (IDS vs IPS)
- Network aliasing for scalable rule management
- Live traffic analysis and log monitoring
- Simulated office network defense architecture

---

## 👤 Author

**Haleema Abid**  
BS Cybersecurity — Air University Kamra Campus  
[0xhaleema.github.io](https://0xhaleema.github.io)
