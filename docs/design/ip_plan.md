# IP Plan — Kelompok 5 B

---

**Skenario:** Simulasi serangan & monitoring pada segmen jaringan terisolasi kelompok, menggunakan Kali Linux sebagai attacker dan Metasploitable 2 sebagai target, dipantau oleh Security Onion.

**Subnet kelompok:** `192.168.5.0/24`

| Hostname | IP Address | OS | Note/Port Target |
| :--- | :--- | :--- | :--- |
| **Target** | `192.168.5.5` | Metasploitable 2 | Port 22 (SSH), 80 (HTTP), 443 (HTTPS), 3306 (MySQL) |
| **Attacker** | `192.168.5.100` | Kali Linux | Attacker Node |
| **Monitoring** | `192.168.5.200` | Security Onion | IDS & Traffic Monitoring |