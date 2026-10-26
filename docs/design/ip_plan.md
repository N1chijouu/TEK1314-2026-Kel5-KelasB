# IP Plan — Kelompok 5 B

---

**Skenario:** Simulasi serangan & monitoring pada segmen jaringan terisolasi kelompok, menggunakan Kali Linux sebagai attacker dan Metasploitable 2 sebagai target, dipantau oleh Security Onion.

**Subnet kelompok:** `192.168.5.0/24`

| Hostname | IP Address | OS | Note/Port Target |
| :--- | :--- | :--- | :--- |
| **Target** | `192.168.5.5` | Metasploitable 2 | Port 22 (SSH), 80 (HTTP), 443 (HTTPS), 3306 (MySQL) |
| **Attacker** | `192.168.5.100` | Kali Linux | Attacker Node |
| **Monitoring** | `192.168.5.200` | Security Onion | IDS & Traffic Monitoring |

---
## Pembaruan Desain Jaringan (Minggu ke-9)

Sesuai dengan *Case Study* PBL, arsitektur dimigrasi dari *Flat Network* (Metasploitable 2) menjadi **Segmentasi Jaringan** berbasis Ubuntu Server agar mereplikasi *tech stack* IoT secara akurat.

**Alasan Perubahan:**
1.  **Target Node:** Menggunakan Ubuntu Server (Nginx, PHP, MySQL) yang jauh lebih representatif untuk simulasi *backend* IoT dibandingkan Metasploitable.
2.  **Network Segmentation:** Pemisahan subnet Attacker dan Target menggunakan Router Linux sebagai *Choke Point* (Firewall terpusat) guna menerapkan prinsip *Defense in Depth*.

**Skema IP Tersegmentasi (Kelompok 5):**
| Node / Peran | IP Address | Gateway | Layanan Utama |
| :--- | :--- | :--- | :--- |
| Router (Attacker) | 10.5.11.1/24 | - | Gateway Segmen A |
| Attacker (Kali) | 10.5.11.10/24 | 10.5.11.1 | Penetration Testing |
| Router (Target) | 10.5.12.1/24 | - | Gateway Segmen B |
| Target (Ubuntu) | 10.5.12.10/24 | 10.5.12.1 | Nginx (80), SSH (2222), MySQL |
| SOC (Onion Mgmt) | 10.5.12.30/24 | 10.5.12.1 | Sguil / Hunt Dashboard |

*Desain Minggu ke-4 di atas tetap dipertahankan sesuai instruksi PBL.*