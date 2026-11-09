# sysadmin-lab-portofolio
My journey to becoming a System Administrator. Hand-on labs, scripts, and projects.
# My SysAdmin Journey
Halo! Saya Ali. Ini adalah dokumentasi perjalanan saya belajar menjadi IT System Administrator.

## Lab 1: Basic System Monitoring Script
- **Tujuan:** Membuat script Bash untuk memonitor resource sistem secara otomatis (Waktu, Disk, RAM, CPU).
- **Tools:** Debian 13, Bash.
- **Hasil:** Berhasil membuat script `cek_sistem.sh` dan mengeksekusinya.
  <img width="802" height="302" alt="gambar" src="https://github.com/user-attachments/assets/15446f01-da9b-4db7-8a67-605154d62005" />

## Lab 2: Hybrid Cloud Monitoring dengan Zabbix
- **Tujuan:** Membangun sistem monitoring terpusat (Zabbix Server) di AWS untuk memantau perangkat *on-premise* (Laptop Debian) dan simulasi jaringan (GNS3).
- **Tools:** AWS EC2, Zabbix 7.0, Debian 13, GNS3, MikroTik, SNMP.
- **Tantangan & Solusi:** 
  Laptop host berada di balik NAT (IP Private). Saya mengatasi ini dengan menerapkan **Zabbix Active Checks**. Zabbix Agent di laptop dikonfigurasi untuk *push* data keluar menuju IP Public AWS (Port 10051) tanpa perlu membuka port router rumah.
- **Hasil:** 
  Berhasil membuat dashboard monitoring terpusat. Status merah pada node MikroTik adalah bentuk *Alerting* yang valid karena instance GNS3 dimatikan sengaja untuk *cost optimization* (FinOps).

  <img width="1366" height="657" alt="gambar" src="https://github.com/user-attachments/assets/4d851796-1c6b-4379-83db-62c4f331a191" />

## LAB 3: Hybrid Cloud Network Lab (AWS & GNS3)
**Tujuan:** Membangun simulasi infrastruktur perusahaan (3 cabang) yang saling terkomeksi antar cabang dan laptop Administrator *On-Premise* (Laptop Debian) dan *Cloud* (AWS).

**Topologi & Teknologi:**
- **Routing & Switching:** Menggunakan FRRouting (FRR) dan MikroTik di GNS3. Konfigurasi **OSPF Multi-Area** untuk pertukaran rute dinamis antar cabang.
- **Cloud:** Deploy server Ubuntu/Debian di AWS (EC2, VPC, Security Group).
- **VPN (Security):** Menghubungkan AWS VPC dengan router lokal di GNS3 menggunakan **WireGuard Site-to-Site VPN**.
- **Firewall:** Konfigurasi ACL (Access Control List) di MikroTik untuk segmentasi jaringan.

**Dokumentasi & Konfigurasi:**
- Topologi simulasi infrastruktur sebuah perusahaan dengan 3 cabang.
  <img width="1366" height="657" alt="gambar" src="https://github.com/user-attachments/assets/3c3896be-3c22-49cc-8744-b59e6a805cf7" />
- Berhasil remote Node Mikrotik CHR dengan winbox via VPN WireGuard
  <img width="1204" height="738" alt="gambar" src="https://github.com/user-attachments/assets/df976401-defd-424e-a55d-cff1808dc05f" />

## Lab 4: Automated Backup Script & Cronjob (AWS EC2)
- **Tujuan:** Membuat sistem otomatisasi backup file secara berkala pada server Ubuntu di AWS EC2 untuk mencegah kehilangan data.
- **Tools:** AWS EC2 (Ubuntu Server 26.04), Bash Scripting, Cronjob.

**Langkah Implementasi:**
1. Membuat script `auto_backup.sh` menggunakan Bash untuk mengompresi folder target menjadi format `.tar.gz` dengan nama file berbasis *timestamp* (tanggal & jam).
2. Melakukan *troubleshooting* pada script di mana *error* awal terjadi karena mencoba membaca folder `/var/log` yang membutuhkan akses *root*. Solusinya, mengubah target direktori ke folder yang diizinkan (`/home/ubuntu/sysadmin-lab`).
3. Menjadwalkan script berjalan otomatis menggunakan **Cronjob** (`crontab -e`).

**Hasil:**
Script berhasil dieksekusi secara manual dan menghasilkan file backup. 
<img width="799" height="77" alt="gambar" src="https://github.com/user-attachments/assets/936eb174-7eff-4ca3-9344-4c2fceb36dfb" />

**Konfigurasi Cron:**

<img width="802" height="57" alt="gambar" src="https://github.com/user-attachments/assets/9b123922-e929-4dac-8885-09b28b81c842" />
<img width="804" height="171" alt="gambar" src="https://github.com/user-attachments/assets/0e3c56de-5fe6-40ad-ac07-20879333c9cb" />

## Lab 5: Web Server Deployment dengan Docker (AWS EC2)
- **Tujuan:** Melakukan *deployment* Web Server (Nginx) di dalam *Container* menggunakan Docker, dan melakukan kustomisasi halaman web menggunakan *Docker Volumes*.
- **Tools:** AWS EC2 (Ubuntu), Docker, Nginx.

**Langkah Implementasi:**
1. Instalasi Docker Engine pada instance Ubuntu AWS.
2. Menjalankan Nginx Container (`docker run -d -p 80:80`).
3. Melakukan *troubleshooting* dan verifikasi status container menggunakan `docker ps`.
4. Membuat halaman web kustom (`index.html`) di *host* AWS.
5. Menggunakan parameter `-v` (Docker Volume) untuk me-mount file `index.html` lokal ke dalam direktori `/usr/share/nginx/html` di dalam container.

**Hasil:**
Web server Nginx berhasil berjalan di dalam container dan menampilkan halaman web kustom yang dapat diakses melalui IP Public AWS.

<img width="801" height="112" alt="gambar" src="https://github.com/user-attachments/assets/8a3cee44-a10a-476c-a004-f49eea48ceb6" />

<img width="1366" height="742" alt="gambar" src="https://github.com/user-attachments/assets/1cac7d23-b8d6-41fa-a179-52fc00b1bbd8" />
