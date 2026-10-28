# sysadmin-lab-portofolio
My journey to becoming a System Administrator. Hand-on labs, scripts, and projects.
# My SysAdmin Journey
Halo! Saya Ali. Ini adalah dokumentasi perjalanan saya belajar menjadi IT System Administrator.

## Lab 1: Basic System Monitoring Script
- **Tanggal:** 28 Oktober 2026
- **Tujuan:** Membuat script Bash untuk memonitor resource sistem secara otomatis (Waktu, Disk, RAM, CPU).
- **Tools:** Debian 13, Bash.
- **Hasil:** Berhasil membuat script `cek_sistem.sh` dan mengeksekusinya.
- <img width="802" height="302" alt="gambar" src="https://github.com/user-attachments/assets/15446f01-da9b-4db7-8a67-605154d62005" />

## Lab 2: Hybrid Cloud Monitoring dengan Zabbix
- **Tanggal:** 28 Oktober 2026
- **Tujuan:** Membangun sistem monitoring terpusat (Zabbix Server) di AWS untuk memantau perangkat *on-premise* (Laptop Debian) dan simulasi jaringan (GNS3).
- **Tools:** AWS EC2, Zabbix 7.0, Debian 13, GNS3, MikroTik, SNMP.
- **Tantangan & Solusi:** 
  Laptop host berada di balik NAT (IP Private). Saya mengatasi ini dengan menerapkan **Zabbix Active Checks**. Zabbix Agent di laptop dikonfigurasi untuk *push* data keluar menuju IP Public AWS (Port 10051) tanpa perlu membuka port router rumah.
- **Hasil:** 
  Berhasil membuat dashboard monitoring terpusat. Status merah pada node MikroTik adalah bentuk *Alerting* yang valid karena instance GNS3 dimatikan sengaja untuk *cost optimization* (FinOps).

  <img width="1366" height="657" alt="gambar" src="https://github.com/user-attachments/assets/4d851796-1c6b-4379-83db-62c4f331a191" />
