# LOG AKTIVITAS MINGGUAN (PBL KEAMANAN SIBER)
**Kelompok:** Kelompok 05 - Kelas B  

---

### Minggu 1–3: Fase Setup Lingkungan Lab
* **Target:** Instalasi CyberOps VM & Security Onion pada laptop Utama dan Backup serta pembuatan toplogi jaringan.
* **Update:**
  * Berhasil melakukan instalasi VM di Laptop utama dan backup serta berhasil membuat Topologi jaringan yang akan di terapkan.
  * **Kendala:** Beban RAM laptop terbatas saat menjalankan beberapa VM sekaligus.
  * **Solusi:** Alokasi RAM Security Onion disesuaikan menjadi 4GB, Kali Linux 2GB, dan Server Target 1GB agar performa stabil.
* **Artefak:** Seluruh VM berhasil menyala pada virtual environment beserta Topologi dan skenario yang telah dibuat.
    * [topology.png](./docs/design/File%20Topology.png)
    * [SetupVM Laptop Utama](./docs/P2/Laptop-Utama/)
    * [SetupVM Laptop Backup](./docs/P2/Laptop-Backup/)
* **Status:** Selesai.

---

### Minggu 4–5: Konfigurasi Jaringan & Verifikasi Logging (Security Onion)
* **Target:** Setup switch virtual dan verifikasi infrastruktur pemantauan NIDS.
* **Update:**
  * Menghubungkan seluruh VM ke dalam satu segmen jaringan internal (`Lab-Siber`) pada subnet `192.168.5.0/24`.
  * Mengaktifkan antarmuka *Promiscuous Mode (Allow All)* pada Security Onion untuk fungsi pemantauan SPAN/Port Mirroring.
  * Menetapkan IP statis: Kali Linux (`192.168.5.100`), Server Target (`192.168.5.5`), dan Security Onion (`192.168.5.200`).
  * **Verifikasi Logging:** Menguji transmisi ICMP (Ping) dari Kali ke Target dan berhasil memverifikasi rekaman log secara real-time pada dashboard Sguil dan Squert.
* **Artefak:** 
  * [Topology Jaringan](docs/phase-1-baseline/assets/File%20Topology.png)
  * [Verifikasi Logging](docs/phase-1-baseline/assets/security-onion-icmp-log.png)
* **Status:** Selesai.

---

### Minggu 6 : Hardening Review & Penyusunan Repositori
* **Target:** Penguatan sistem keamanan server target (*Before Attack*) dan pembuatan baseline documentation.
* **Update:**
  * Melakukan audit port terbuka menggunakan perintah `ss -tulpn`.
  * **System Hardening:** Menonaktifkan layanan rentan yang tidak diperlukan, yaitu Telnet (`xinetd` / Port 23) dan FTP (`vsftpd` / Port 21).
  * **Network Hardening:** Mengaktifkan Firewall UFW dengan kebijakan *Default Deny Incoming*, dan hanya mengizinkan port esensial (Port 22 SSH, 80 HTTP, 443 HTTPS).
  * Menyesuaikan identitas standar hostname server menjadi `SRV-WEB-KEL05B`.
  * Menginisialisasi struktur folder repositori GitHub PBL (`/docs/phase-1-baseline/`) dan menyusun draft laporan `baseline-report.md`.
* **Artefak:** 
  * [ufw-status](docs/phase-1-baseline/assets/ufw-status.png)
  * [baseline-report](docs/phase-1-baseline/baseline-report.md)
* **Status:** Selesai.

---