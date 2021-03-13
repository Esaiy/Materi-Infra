# Instalasi Linux

## Sub-materi
- [Instalasi Linux](#instalasi-linux)
  - [Sub-materi](#sub-materi)
    - [1. Persiapan](#1-persiapan)
    - [2. Teknik Instalasi](#2-teknik-instalasi)
    - [3. Membuat Virtual Machine](#3-membuat-virtual-machine)
    - [4. Instalasi Ubuntu Server 20.04](#4-instalasi-ubuntu-server-2004)
        - [Referensi](#referensi)

### 1. Persiapan
- File ISO Ubuntu 20.04 LTS ([Download](https://ubuntu.com/download/server))
- Installer VirtualBox ([Download](https://www.virtualbox.org/wiki/Downloads))

### 2. Teknik Instalasi
Jika hendak menggunakan lebih dari satu sistem operasi atau sering disebut OS(operating system) pada suatu komputer biasanya ada dua pilihan teknik instalasi, yaitu **dual-boot** atau **virtualisasi**.
**Dual-boot** adalah teknik menginstall dua atau lebih OS pada satu komputer, dimana masing-masing OS berjalan secara mandiri. Pengguna hanya dapat menggunakan salah satu OS dalam satu watu, dengan cara memilih OS yang akan dipakai ketika menyalakan komputer.<br/>

Sedangkan **Virtualisasi** adalah teknik menginstal dan menjalankan suatu OS di atas OS lain sebagai host, yaitu dengan menggunakan program berjenis mesin virtual (virtual machine), salah satu contohnya adalah VirtualBox. Dengan mesin virtual ini, pengguna dapat menjalankan suatu OS, sebagai contoh Linux, pada saat OS lain berjalan, sebagai contoh Windows, sehingga pengguna dapat menjalankan beberapa OS sekaligus dalam satu waktu.

Berikut ini perbandingan termasuk kelebihan dan kekurangan dari kedua teknik instalasi tersebut:

|Dual-Boot|Virtual Machine|
|---|---|
|Secara umum lebih cepat, karena masing - masing OS berjalan secara mandiri|Secara umum lebih lambat, karena harus berbagi sumber daya prosesor dan memori dengan OS host|
|Kedua OS dapat bertukar data dengan mudah, asalkan saling mendukung format sistem file pada harddisk|Bertukar file antar OS tidak dapat dilakukan secara langsung, perlu beberapa konfigurasi|
|Hanya dapat menjalankan salah satu OS saja pada satu waktu|Dapat menjalankan beberapa OS sekaligus dalam satu waktu(asal spesifikasi komputer mencukupi)|
|Prosedur instalasi dan konfigurasi untuk dual-booting cukup rumit dan beresiko (kehilangan data), terutama pada saat partisi harddisk|Prosedur instalasi OS menjadi mudah tanpa harus bingung dengan hal-hal teknis seperti partisi harddisk|
|Ideal untuk penggunaan sehari-hari, yang membutuhkan performa penuh komputer|Ideal untuk sekedar mengetes suatu OS, atau sekedar menjalankan suatu program yang tidak dapat berjalan pada OS host|
|Jika terjadi kerusakan pada salah satu OS, ada kemungkinan berpengaruh dengan OS satunya|Kerusakan pada OS yang di virtualisasikan tidak akan berpengaruh pada OS host|

### 3. Membuat Virtual Machine

1. Install Oracle VM VirtualBox. Jika sudah ada, lanjut ke langkah 2.<br/><br/>
2. Buka aplikasi Oracle VM VirtualBox di Windows kamu.<br/><br/>
![Tampilan awal Oracle VM VirtualBox](./img/tampilan-awal.png "Tampilan awal Oracle VM VirtualBox")
<br/><br/>
3. Klik **New** untuk membuat Virtual Machine baru. Isi **name** dengan nama 'Ubuntu 20.04', **type** pilih Linux, dan pilih **version** sesuai sepesifikasi PC atau Laptop kamu. Kemudian klik **Next** untuk proses selanjutnya.<br/><br/>
![Membuat Virtual Machine baru Oracle VM VirtualBox](./img/1.png "Membuat Virtual Machine baru Oracle VM VirtualBox")
<br/><br/>
4. Selanjutnya kamu disuruh untuk menentukan besaran memori, namun VirtualBox otomatis merekomendasikan besarnya memori. Jika sudah sesuai klik **Next**.<br/><br/>
![Set memori VM baru Oracle VM VirtualBox](./img/2.png "Set memori VM baru Oracle VM VirtualBox")
<br/><br/>
5. Selanjutnya kamu disuruh untuk menentukan ukuran harddisk, namun VirtualBox otomatis merekomendasikan ukuran harddisk. Jika sudah sesuai klik **Next**.<br/><br/>
![Set ukuran harddisk VM baru Oracle VM VirtualBox](./img/3.png "Set ukuran harddisk VM baru Oracle VM VirtualBox")
<br/><br/>
6. Klik **Next** saja pada proses ini untuk menuju proses selanjutnya.<br/><br/>
![Set tipe harddisk VM baru Oracle VM VirtualBox](./img/4.png "Set tipe harddisk VM baru Oracle VM VirtualBox")
<br/><br/>
7. Klik **Next** saja pada proses ini untuk menuju proses selanjutnya.<br/><br/>
![Set tipe harddisk VM baru Oracle VM VirtualBox(2)](./img/5.png "Set tipe harddisk VM baru Oracle VM VirtualBox(2)")
<br/><br/>
8. Menentukan ukuran harddisk(direkomendasikan minimal 10GB). Klik **Create**.<br/><br/>
![Set ukuran harddisk VM baru Oracle VM VirtualBox(3)](./img/6.png "Set ukuran harddisk VM baru Oracle VM VirtualBox(3)")
<br/><br/>
9. Yee, virtual machine yang kamu buat sudah jadi! Namun, kamu masih harus menginstall Ubuntu 20.04 pada virtual machine yang telah kamu buat.

### 4. Instalasi Ubuntu Server 20.04
Setelah berhasil membuat virtual machine, selanjutnya kita menginstall Ubuntu 20.04 pada virtual machine yang telah dibuat.

1. Pilih virtual machine yang ingin di install, lalu klik **Setting** -> **Storage** -> **Controller: IDE** -> **Empty** -> **Choose Virtual Optical Disk File** untuk memilih file ISO Ubuntu yang akan di install. Kemudian klik **Start**(tanda panah hijau)  <br/><br/>
![Set file ISO Ubuntu VM baru Oracle VM VirtualBox](./img/7.png "Set file ISO Ubuntu VM baru Oracle VM VirtualBox")<br/><br/>
![Set file ISO Ubuntu VM baru Oracle VM VirtualBox(2)](./img/8.png "Set file ISO Ubuntu VM baru Oracle VM VirtualBox(2)")<br/><br/>
![Set file ISO Ubuntu VM baru Oracle VM VirtualBox(3)](./img/9.png "Set file ISO Ubuntu VM baru Oracle VM VirtualBox(3)")
<br/><br/>

1. File ISO Ubuntu sudah berjalan. Selanjutnya tinggal ikuti langkah instalasinya. Pilih **Ubuntu Server**.<br/><br/>
![Instalasi Ubuntu(1)](./img/11.png "Instalasi Ubuntu(1)")
<br/><br/>
3. Memilih bahasa yang digunakan untuk penyesuaian keyboard. Ikuti saja defaultnya, langsung klik **Continue**.<br/><br/>  
![Instalasi Ubuntu(5)](./img/12.png "Instalasi Ubuntu(5)")
<br/><br/>
1. Tekan Enter bila ingin melakukan update installer.<br/><br/>
![Instalasi Ubuntu(3)](./img/13.png "Instalasi Ubuntu(3)")
<br/><br/>
5. Pilih layout keyboard yang diinginkan<br/><br/>
![Instalasi Ubuntu(4)](./img/14.png "Instalasi Ubuntu(4)")
<br/><br/>
1. Jika sistem terhubung ke jaringan, harusnya akan ada alamat IP dari server DHCP Anda.<br/><br/>
![Instalasi Ubuntu(5)](./img/15.png "Instalasi Ubuntu(5)")
<br/><br/>
7. Pilih **Guided storage configuration** agar pembagian disk dilakukan secara otomatis.<br/><br/>
![Instalasi Ubuntu(6)](./img/16.png "Instalasi Ubuntu(6)")
<br/><br/>
8. Tekan Enter apabila kita ingin mengatur pembagiannya lagi.<br/><br/>
![Instalasi Ubuntu(7)](./img/17.png "Instalasi Ubuntu(7)")
<br/><br/>
9. Pilih continue untuk memulai proses instalasi<br/><br/>
![Instalasi Ubuntu(8)](./img/18.png "Instalasi Ubuntu(8)")
<br/><br/>
10. Lakukan setup profile user dengan mengisikan nama, nama server, username, dan password<br/><br/>
![Instalasi Ubuntu(9)](./img/19.png "Instalasi Ubuntu(9)")
<br/><br/>
11.  Centang bagian **Install OpenSSH server** agar bisa melakukan koneksi ssh pada server kita.<br/><br/>
![Instalasi Ubuntu(10)](./img/20.png "Instalasi Ubuntu(10)")
<br/><br/>
12.  Ini adalah list environment server populer yang bisa kita pilih untuk install, untuk sekarang bisa kita skip dulu.<br/><br/>
![Instalasi Ubuntu(11)](./img/21.png "Instalasi Ubuntu(11)")
<br/><br/>
13.  Terakhir bisa kita tunggu hingga proses instalasi selesai.<br/><br/>
![Instalasi Ubuntu(12)](./img/22.png "Instalasi Ubuntu(12)")
<br/><br/>

##### Referensi
- Modul Pelatihan Linux 2020
- https://abrari.wordpress.com/2009/12/12/dual-booting-vs-virtualisasi/
- https://id.wikihow.com/Memasang-Ubuntu-di-VirtualBox
- https://www.ubuntu.com/
- https://www.virtualbox.org/