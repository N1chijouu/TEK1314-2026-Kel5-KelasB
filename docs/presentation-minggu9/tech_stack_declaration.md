# Deklarasi Tech Stack dan Replikasi Target Node
**Kelompok 5 - TEK1314 Keamanan Siber**

Sesuai dengan panduan PBL, kami mendeklarasikan pemetaan teknologi dari proyek IoT asli ke lingkungan replika (Target Node) di lab virtual. Replikasi ini disesuaikan dengan keterbatasan *resource* tanpa menghilangkan esensi pengujian keamanan.

| Komponen | Teknologi pada Proyek IoT Asli | Direplikasi sebagai (Target Node) | Justifikasi Replikasi |
| :--- | :--- | :--- | :--- |
| **Sistem Operasi Backend** | Debian | Ubuntu Server | Ubuntu merupakan *derivative* Debian. Perintah sistem, manajemen paket (APT), dan konfigurasi keamanan (UFW, SSH) identik. |
| **Database / Penyimpanan** | PostgreSQL | MySQL | MySQL lebih ringan untuk *resource* VM. Replikasi tetap mempertahankan arsitektur *Relational Database* dan pengujian *Least Privilege* user. |
| **Protokol Komunikasi Sensor** | MQTT | HTTP REST (via PHP) | Mengakomodasi keterbatasan lab. HTTP REST mereplikasi alur pengiriman data sensor dari *edge device* ke *backend* (metode POST). |
| **Dashboard / Monitoring** | Vue.js / Thingsboard | Custom PHP Dashboard | Menghemat RAM VM. PHP Dashboard mereplikasi fungsionalitas utama: endpoint API penerima data dan visualisasi data sensor. |