# Attack Plan Fase 2 (Red Team)
**Kelompok 5 - TEK1314 Keamanan Siber**
**Target Node Replika:** 10.5.12.10 (Ubuntu Server - Backend KABITA)

Rencana serangan ini disusun berdasarkan kerentanan potensial pada replika sistem IoT. Seluruh skenario menyasar Target Node replika yang terisolasi di lab virtual.

## Skenario 1: Reconnaissance (Pemetaan Jaringan)
- **Kategori:** Reconnaissance
- **Teknik:** Port/service scanning dan OS fingerprinting.
- **Tools:** Nmap, Wireshark.
- **Target:** IP 10.5.12.10 (Seluruh rentang port).
- **Tujuan:** Mengidentifikasi port yang terbuka, layanan yang berjalan, dan versi sistem operasi target.
- **Ekspektasi:** Menemukan port 2222 (SSH) dan port 80 (HTTP Nginx). Aktivitas ini akan memicu alert ET SCAN pada sensor Snort di Security Onion.
- **Relevansi:** Tahap awal untuk memetakan attack surface sebelum melakukan eksploitasi lebih lanjut.

## Skenario 2: Exploitation / Akses (SSH Brute-force)
- **Kategori:** Exploitation / Akses
- **Teknik:** Brute-force / Dictionary Attack pada layanan remote.
- **Tools:** Hydra.
- **Target:** Port 2222 (Layanan SSH) di 10.5.12.10.
- **Tujuan:** Mencoba menebak kredensial user untuk mendapatkan akses ke dalam server (Remote Access).
- **Ekspektasi:** Serangan akan gagal total. Server telah dikonfigurasi dengan `PasswordAuthentication no` dan mewajibkan SSH Key-based Authentication. Server akan merespons dengan `Permission denied (publickey)`.
- **Relevansi:** Menguji efektivitas mitigasi akses (Kategori A) yang telah diterapkan pada Fase 1.

## Skenario 3: Availability (SYN Flood DoS)
- **Kategori:** Availability (Maksimal 1 dari 3 skenario)
- **Teknik:** SYN Flood / Denial of Service sederhana pada 1 layanan.
- **Tools:** hping3 (skala lab, terkontrol).
- **Target:** Port 80 (Web Server Nginx) di 10.5.12.10.
- **Tujuan:** Membanjiri layanan web dengan paket SYN untuk menguji ketahanan server dan menghabiskan resource koneksi (TCP backlog).
- **Ekspektasi:** Layanan web akan melambat atau tidak dapat diakses sementara. Aktivitas ini akan memicu alert traffic anomali (S0) di log Zeek/Snort Security Onion.
- **Relevansi:** Menguji aspek ketersediaan (Availability) dari sistem Backend IoT KABITA jika mendapat serangan DoS.