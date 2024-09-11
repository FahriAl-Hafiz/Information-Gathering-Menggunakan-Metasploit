# Information-Gathering-Menggunakan-Metasploit
*EDUCATION PURPOSE

# Menjalankan Metasploit

  service postgresql start: Memulai service PostgreSQL yang diperlukan oleh Metasploit untuk mengelola database hasil scanning.
   
   msfconsole: Menjalankan Metasploit Framework.
   
   db_status: Mengecek status koneksi Metasploit dengan PostgreSQL.
   
    Jika koneksi gagal:
        msfdb init: Menginisialisasi database PostgreSQL untuk Metasploit.
        service postgresql restart: Me-restart PostgreSQL untuk memastikan koneksi terhubung kembali.

Hasil yang diharapkan:

    [*] Connected to msf. Connection type: postgresql.: Koneksi database berhasil.

![image](https://github.com/user-attachments/assets/17525bd4-977d-47b1-9680-b086016e2180)

![image](https://github.com/user-attachments/assets/27b3ee2b-83f1-45de-a625-22ed36e2eb27)

mencari ip , disini akan ip website www.dpr.go.id dengan menggununakan tool nslookup

![image](https://github.com/user-attachments/assets/0ec0dcf1-6ef9-4701-a5ea-7d5489e9d46f)

# Mencari Host yang Aktif (Alive Hosts)

  nPenjelasan:

  -Pn: Mengabaikan ping dan langsung memindai host, berguna jika host tidak merespons ping.
  
   -sS: Melakukan SYN scan untuk mendeteksi port yang terbuka.
   
   -O: Deteksi Operating System.
   
   -oX Test: Menyimpan hasil scan dalam format XML dengan nama file Test.
   
   192.168.251.9: Alamat IP target yang akan dipindai.
      
![image](https://github.com/user-attachments/assets/9ee42792-191b-47d9-a95d-73c9eeb5747f)

db_import Test: Mengimpor hasil pemindaian Nmap ke dalam database Metasploit.
    
hosts: Menampilkan daftar host yang ditemukan beserta detail OS, IP, dan MAC address.

![image](https://github.com/user-attachments/assets/467294b8-a1e3-4c69-9451-c27aed9eb2d1)

# Memeriksa Detail Host Tertentu

db_nmap -sS -A 223.255.230.144: Melakukan scan mendalam pada host 223.255.230.144 dengan:

  -sS: SYN scan untuk memindai port.
  
   -A: Deteksi OS, versi layanan, dan traceroute.

![image](https://github.com/user-attachments/assets/d11f78f6-7b41-4b4c-ab6c-a5f3aeead36f)

db_services atau services: Menampilkan daftar layanan yang berjalan di host tersebut.

![image](https://github.com/user-attachments/assets/e7bf0048-65e1-4a7a-b698-b201117a53ce)

# Scan Port Terbuka dan Layanan

search portscan: Mencari module port scanning di Metasploit.

  Beberapa module portscan ditemukan, seperti:
        scanner/portscan/syn: Menggunakan SYN scan untuk mencari port terbuka.
        scanner/portscan/tcp: Melakukan pemindaian semua port TCP.

![image](https://github.com/user-attachments/assets/e66bf078-65e2-4acb-b676-1232910dc371)

use scanner/portscan/syn: Memilih modul portscan SYN.

show options: Melihat konfigurasi default modul yang dipilih, seperti jumlah thread, delay, target IP, dll.

![image](https://github.com/user-attachments/assets/67460eb4-b965-4348-8783-d5dfd0c0d46c)

set RHOSTS 223.255.230.144: Mengatur target IP yang akan dipindai.

set THREADS 100: Mengatur jumlah thread untuk meningkatkan kecepatan pemindaian.

run: Menjalankan pemindaian untuk memeriksa port yang terbuka pada target 223.255.230.144

![image](https://github.com/user-attachments/assets/95856a0c-b02b-43d7-b548-2d0230590bf3)

# Mencari dengan Versi SMB

  use scanner/smb/smb_version: Memilih modul untuk mendeteksi versi SMB.
  
   set RHOSTS 10.0.2.23: Menetapkan target IP.
   
   set THREADS 100: Menambah thread untuk mempercepat proses pemindaian.
   
   run: Menjalankan modul untuk memeriksa versi SMB yang aktif pada target.

   jalankan perintah hosts, perhatikan kolom os dari host yang sudah Anda scan.

![image](https://github.com/user-attachments/assets/e97995ed-b35e-4ac7-b727-bf3847826b56)

