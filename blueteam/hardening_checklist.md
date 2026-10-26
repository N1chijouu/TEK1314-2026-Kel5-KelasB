# Hardening Checklist (Standar Minimum Fase 2)
**Kelompok 5 - TEK1314 Keamanan Siber**
**Target Node:** 10.5.12.10 (Ubuntu Server - Replika Backend KABITA)

| No | Kategori | Kontrol Keamanan | Status | Bukti (Evidence) |
| :--- | :--- | :--- | :--- | :--- |
| **1** | **A. Access & Authentication** | Mengganti port default SSH dari 22 menjadi 2222 | Selesai | `ssh_after.png` (Port 22 closed, 2222 open) |
| **2** | **A. Access & Authentication** | Menonaktifkan login langsung sebagai user root (`PermitRootLogin no`) | Selesai | `ssh_after.png` (Permission denied) |
| **3** | **A. Access & Authentication** | Mewajibkan SSH Key-based Authentication (`PasswordAuthentication no`) | Selesai | `ssh_key_success.png` (Login sukses tanpa password) |
| **4** | **B. Service & Attack Surface** | Menonaktifkan layanan/port yang tidak digunakan (CUPS/Port 631 dan mDNS/Port 5353) | Selesai | `port_audit.png` (`ss -tulpn` port tidak muncul) |
| **5** | **B. Service & Attack Surface** | Mengaktifkan Firewall UFW dengan prinsip Default Deny (Whitelist Port 2222, 80, 443) | Selesai | `ufw_status_active.png` |
| **6** | **B. Service & Attack Surface** | Melakukan Update & Patch OS (`apt update && apt upgrade`) | Selesai | `apt_upgrade.png` (Sistem up-to-date) |
| **7** | **B. Service & Attack Surface** | Menghapus/menghindari kredensial default (Tidak menggunakan user `root` untuk koneksi aplikasi web) | Selesai | `mysql_least_privilege.png` (User `webapp` digunakan) |
| **8** | **C. Data & Application** | Menerapkan Least Privilege pada user Database (User `webapp` hanya bisa SELECT, INSERT, UPDATE) | Selesai | `mysql_least_privilege.png` (Gagal saat uji DROP TABLE) |
| **9** | **C. Data & Application** | Menerapkan Validasi Input pada API Endpoint (`is_numeric`) untuk mencegah injeksi data palsu | Selesai | `api_validation_denied.png` (Error: Suhu harus berupa angka) |
| **10** | **C. Data & Application** | Mencegah SQL Injection menggunakan Prepared Statements pada form pencarian web | Selesai | `web_sqli_failed.png` (Payload SQLi tidak tereksekusi) |
| **11** | **C. Data & Application** | Mengaktifkan Logging aktivitas mencurigakan (Security Onion/Snort memantau traffic ke Target Node) | Selesai | `sguil_detect_nmap.png` (Alert ET SCAN muncul) |
| **12** | **C. Data & Application** | Mengunci akses Database (Bind Address ke 127.0.0.1) agar tidak terekspos ke jaringan luar | Selesai | `port_audit_db.png` (MySQL hanya listen di localhost) |
