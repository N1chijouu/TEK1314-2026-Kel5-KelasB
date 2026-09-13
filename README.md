# It's TEK1314-2026-Kel5-KelasB

Selamat datang di Repository TEK1314-2026-Kel5-KelasB.<br>
kami beranggotakan :
- Sebastian Boanerges [J0404241030] (Lead)
- Ahmad Faliansyah [J0404241110] (Red Team)
- Pandu Akmal Fauzan [J0404241047] (Blue Team)
- Muhammad Fauzia [J0404241151] (Blue Team)
<hr>

## Deskripsi Skenario Perancangan Jaringan dan Pengujian Keamanan

### 1. Ringkasan Skenario
Pada perancangan arsitektur jaringan ini, dirancang sebuah lingkungan laboratorium simulasi keamanan siber yang beroperasi pada segmen IP *192.168.5.0/24. Skenario ini bertujuan untuk mensimulasikan aktivitas pengujian penetrasi (*penetration testing*) oleh pihak penyerang serta mekanisme pemantauan lalu lintas jaringan secara langsung (*real-time network monitoring) oleh pihak pemantau.

### 2. Skenario Penyerangan dan Pemantauan
* *Aktivitas Penyerangan (Red Team)*: 
  Node Penyerang (Attacker) mengoperasikan sistem operasi Kali Linux dengan alamat IP 192.168.5.100 melalui antarmuka FastEthernet0/1 pada sakelar (Switch). Penyerang melakukan pemindaian port (port scanning) dan identifikasi kerentanan pada Server Target (192.168.5.5) yang mengoperasikan Metasploitable 2 via antarmuka FastEthernet0/2. Fokus pengujian meliputi eksplorasi celah keamanan pada layanan yang aktif, seperti port 80/443 (HTTP/HTTPS), port 22 (SSH), dan port 3306 (MySQL).

* *Aktivitas Pemantauan Keamanan (Blue Team)*: 
  Node Pemantau (Monitoring) mengoperasikan Security Onion dengan alamat IP 192.168.5.200 yang terhubung pada port FastEthernet0/3. Sakelar (Switch) dikonfigurasi menggunakan fitur Port Mirroring (SPAN) untuk menduplikasi seluruh data lalu lintas yang berasal dari port FastEthernet0/1 dan FastEthernet0/2 ke port FastEthernet0/3. Hal ini memungkinkan Node Pemantau untuk menganalisis paket data, mencatat log aktivitas, serta mendeteksi indikasi serangan tanpa mengganggu alur komunikasi utama jaringan.

### 3. Detail Dokumentasi Arsitektur
Informasi lengkap mengenai rancangan topologi dan alokasi alamat IP dapat diakses pada direktori proyek berikut:
* [docs/design/topology.png](docs/design/File%20Topology.png) (Diagram Visual Topologi Jaringan)
* [docs/design/ip_plan.md](docs/design/ip_plan.md) (Spesifikasi Skema Alokasi IP Address dan Port Service)