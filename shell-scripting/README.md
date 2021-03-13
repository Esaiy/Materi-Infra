# Shell Scripting

## Outline

1. [Shell Scripting](#1-shell-scripting)
    - [1.1 Pemrograman Shell](#11-pemrograman-shell)
    - [1.2 Perintah Dasar Shell](#12-perintah-dasar-shell)
    - [1.3 Simple Shell Script](#13-simple-shell-script)
    - [1.4 Variabel](#14-variabel)
        - [1.5.1 Special Variable](#141-special-variable)
    - [1.5 Input Output](#15-input-output)
    - [1.6 Quoting](#16-quoting)
    - [1.7 Operator Dasar](#17-operator-dasar)
        - [1.7.1 Operator Aritmatika](#171-operator-aritmatika)
        - [1.7.2 Operator Relasional](#172-operator-relasional)
    - [1.8 Conditional Statement](#18-conditional-statements)
        - [1.8.1 If...Else](#181-ifelse)
        - [1.8.2 Case](#182-case)
    - [1.9 Loop](#19-loop)
        - [1.9.1 While Loop](#191-while-loop)
        - [1.9.2 For Loop](#192-for-loop)
        - [1.9.3 Until Loop](#193-until-loop)
        - [1.9.4 Select Loop](#194-select-loop)
        - [1.9.5 Nesting Loop](#195-nesting-loop)
    - [1.10 Function](#110-function)
        - [1.10.1 Nested Functions](#1101-nested-functions)
2. [Referensi](#referensi)

# 1. Shell Scripting
## 1.1 Pemrograman Shell
Pemrograman shell adalah menyusun beberapa perintah shell (internal maupun eksternal) menjadi serangkaian perintah untuk melakukan tugas tertentu.

Pemrograman shell di Unix/Linux juga disebut dengan shell scripting. Untuk memudahkan, shell script dapat disimpan ke dalam sebuah file yang dapat dieksekusi kapanpun kita inginkan.
    
Manfaat belajar shell scripting:

- Dapat bekerja secara efektif dan efisien karena tidak perlu mengetik serangkaian perintah secara berulang-ulang, cukup menulis dan mengeksekusi satu file saja

- Dapat menjalankan beberapa perintah sebagai satu perintah

- Dapat menjalankan perintah secara otomatis
## 1.2 Perintah Dasar Shell
-- insert common knowledge here --

Ada beberapa karakter yang cukup penting untuk digunakan dalam shell:

- __Redirection__ (mengirim output ke file atau menerima input dari file) menggunakan operator redirect >, >>, <, contoh:

```bash
ls /home/Documents > test.txt
#hasil output ls dari directori /home/Documents dikirim ke file test.txt. jika file belum ada akan dibuat, tetapi jika sudah ada, isinya akan ditimpa

ls /home/Documents >> test.txt
#hampir sama, bedanya jika file sudah ada maka isinya akan ditambah di akhir file

sort < test.txt
#file test.txt dijadikan input oleh perintah sort
```

- __Pipe__ (output suatu perintah menjadi input perintah lain) menggunakan operator |, contoh:
```bash
ls -l | sort -s
#ouput perintah ls -l menjadi input perintah sort -s (urutkan secara descending)
```
- __Wildcard__ menggunakan karakter *, ?, [ ], contoh:
```bash
ls a*
#tampilkan semua file yang dimulai dengan a

ls a?a
#tampilkan file yang dimulai dengan a, kemudian sembarang karakter tunggal, dan diakhiri dengan a

ls [re]*
#tampilkan file yang dimulai dengan salah satu karakter r atau e
```
Untuk melihat informasi selengkapnya tentang bash shell, silahkan membuka manual bash dengan cara:

```bash
$ man bash
```

## 1.3 Simple Shell Script
Buatlah sebuah file berekstensi `.sh` menggunakan text editor pilihan kalian! Misalnya nano, vi, atau gedit.

Misalnya:
```
$ nano hello.sh
```

Tulis beberapa baris perintah disana, diawali dengan shebang dan interpreter yang akan digunakan, di sini tentunya adalah bash, `#!/bin/bash`. 

Shebang berfungsi untuk memberitahu sistem bahwa perintah-perintah yg ada di dalam file tersebut harus dijalankan dengan interpreter yang dituliskan setelah shebang.

```bash
#!/bin/bash
echo "Hello, world!"
```

Simpan dan ubah permission file script agar dapat dieksekusi.
```bash
$ chmod +x hello.sh
```
Eksekusi file script dengan cara ./nama_file.sh atau `bash nama_file.sh`.

![hello world](/gambar/1.4.png)

## 1.4 Variabel
- Beberapa hal yang perlu diperhatikan dalam mendefinisikan variabel:

    i. Nama variabel hanya boleh terdiri dari:
    - Huruf (a-z dan A-Z)
    - Angka (0-9)
    - Karakter underscore (_)
    
    ii.  Nama variabel dimulai dengan huruf atau underscore
    
    iii. Tidak boleh menggunakan karakter spesial seperti !, *, $, #, -, dll karena karakter tersebut punya makna khusus untuk shell

    iv. Bersifat case sensitive (membedakan huruf besar dan kecil)

- Syntax

    - Mendefinisikan variabel
    ```
    nama_var=nilai
    ```
    - Mengakses variabel
    ```
    $nama_var
    ```
- Tipe-Tipe Variabel
    - String
    ```
    nama_var="string"
    ```
    - Integer
    ```
    nama_var=nilai
    ```
    - Array
        
        #Jika isi array berupa string
    
        nama_var=("string0" "string1" "string2" ... "stringN")

        #Jika isi array berupa integer
        
        nama_var=(nilai0 nilai1 nilai2 ... nilaiN)    

Contoh:
```bash
#!/bin/bash

laboratorium="Arsitektur dan Jaringan Komputer"
jumlah_admin=4
nama_admin=("Kuuhaku" "Esaiy" "Steven" "Manis")

echo "Variabel string:" $laboratorium
echo "Variabel integer:" $jumlah_admin
echo "Variabel array pertama:" ${nama_admin[0]}
```
Output:

![variabel](/gambar/bash1-5.png)


### 1.4.1 Special Variable
Beberapa special variable yang sering dipakai:

| Variable                                        | Deskripsi                                                                            |
| --------------------------------------------------------- |:--------------------------------------------------------------------------------------- |
|   $0   | Berisi nama file script yang sedang dijalankan
|   $n   | n disini adalah angka desimal positif yang sesuai dengan posisi argumen (argumen pertama adalah $1, argumen kedua adalah $2, dst)
|   $#   | Jumlah argumen yang diinput pada script
|   $*   | Semua argumen $n
|   $?   | Status exit dari perintah terakhir yang dijalankan
|   $$   | Proses ID (PID) shell saat ini


Contoh:
```bash
#!/bin/bash

echo "Nama script : $0"
echo "Argumen ke-1 : $1"
echo "Argumen ke-2 : $2"
echo "Hai $1, selamat datang di materi camin $2!"
echo "Total argumen : $#"
echo "Semua argumen : $*"
echo "PID : $$"
```
Output:

![special](/gambar/special.png)

## 1.5 Input Output
- read digunakan untuk mengambil input dari keyboard dengan syntax sebagai berikut:

    `read nama_var`

- echo digunakan untuk menampilkan output dengan syntax sebagai berikut:

    #Menampilkan teks biasa

    `echo "teks"`

    #Menampilkan isi dari sebuah variabel

    `echo $nama_var`

Catatan:

Jika ingin menggunakan new line character (\n) pada echo, gunakan echo -e "teks\n teks"

Contoh:
```bash
#!/bin/bash

laboratorium="Arsitektur dan Jaringan Komputer"

echo "Siapa namamu?"
read nama
echo -e "\nHai $nama!\nSelamat datang di materi camin $laboratorium ! ;)"
```
Output:


![input](/gambar/inp.png)

Selain echo, bash juga menyediakan perintah builtin printf untuk menampilkan output dengan format tertentu, mirip bahasa C. Contoh:
```bash
#!/bin/bash

laboratorium="AJK";
angka=12;

printf "Ini enter\n\tdi bash\n";
printf "Laboratorium apa? %s\n" $laboratorium;
printf "%d decimal dalam float = %.2f\n" $angka $angka
```
Output:

![printf](/gambar/printf.png)

## 1.6 Quoting
Shell Unix/Linux memiliki beberapa karakter spesial yang disebut dengan **metakarakter**. Karakter tersebut punya makna khusus jika digunakan di dalam shell script. Beberapa macam metakarakter:
```bash
* ? [ ] ' " \ $ ; & ( ) | ^ < > new-line space tab
```

Ada 4 jenis **quoting**, yaitu:

| No | Quoting | Deskripsi|
|---|---|---|
| 1 | Single Quote (') | Semua metakarakter di antara single quote akan kehilangan makna khusus |
| 2 | Double Quote (") | Sebagian besar metakarakter di antara double quote akan kehilangan makna khusus, kecuali `$, backquote, \$, \', \", \\` |
| 3 | Backslash (\\) | Karakter apa pun setelah backslash akan kehilangan makna khusus |
| 4 | Backquote (`) | Apa pun di antara back quote akan diperlakukan sebagai perintah dan akan dieksekusi |

Contoh:   
```bash
#!/bin/bash

single=3

#Single quote
echo '$single'

#Double quote
echo "$single"

#Backslash
echo \<-\$1500.\*\*\>\; \(update\?\) \[y\|n\]

#Backquote
dmn=`pwd`
echo "Dimana kita? " $dmn
```

Output:   
![hasil-quote](/gambar/hasil-quote.png)

Lebih banyak dapat dilihat sendiri di `man bash`

## 1.7 Operator Dasar
Ada beberapa jenis operator yang didukung oleh shell, yaitu:
  1. Operator Aritmatika
  2. Operator Relasional
  3. Operator Boolean
  4. Operator String
  5. Operator File Test

Namun yang akan dibahas lebih jauh hanyalah operator **aritmatika** dan **relasional**.

### 1.7.1 Operator Aritmatika

| No | Operator | Deskripsi |
|---|---|---|
| 1 | + | Penjumlahan |
| 2 | - | Pengurangan |
| 3 | * | Perkalian |
| 4 | / | Pembagian |
| 5 | % | Modulus (sisa pembagian) |
| 6 | = | Menempatkan nilai di sisi kanan ke variabel di sisi kiri |
| 7 | == | Membandingkan 2 nilai yang sama |
| 8 | != | Membandingkan 2 nilai yang tidak sama |

Ada 3 cara yang dapat digunakan untuk melakukan operasi matematika, yaitu:
1. Menggunakan perintah built-in **let**
2. Menggunakan perintah eksternal **expr** 
3. Menggunakan perintah subtitusi ` $((ekspresi))`

Contoh:   
```bash
#!/bin/bash

a=15
b=7

#memakai let
let jumlah=$a+$b
let kurang=$a-$b
let kali=$a*$b

#memakai expr
bagi=`expr $a / $b`

#memakai perintah subtitusi $((ekspresi))
mod=$(($a % $b)) 

echo "a + b = $jumlah"
echo "a - b = $kurang"
echo "a * b = $kali"
echo "a / b = $bagi"
echo "a % b = $mod"

b=$a

echo "a = $a"
echo "b = $b"
```

Output:

![hasil-181](/gambar/hasil-181.png)

### 1.7.2 Operator Relasional

| No | Operator | Deskripsi | 
|---|---|---|
| 1 | -eq | Memeriksa apakah nilai kedua operan sama (==) |
| 2 | -ne | Memeriksa apakah nilai kedua operan tidak sama (!=) |
| 3 | -gt | Memeriksa apakah nilai operan kiri lebih besar daripada operan kanan (>) |
| 4 | -lt | Memeriksa apakah nilai operan kiri lebih kecil daripada operan kanan (<)  |
| 5 | -ge | Memeriksa apakah nilai operan kiri lebih besar atau sama dengan operan kanan (>=) |
| 6 | -le | Memeriksa apakah nilai operan kiri lebih kecil atau sama dengan operan kanan (<=) |

Operator relasional biasanya digunakan bersama dengan conditional statements, contoh:   
```bash
#!/bin/bash

a=15
b=7

if [ $a -eq $b ]
then
  echo "$a -eq $b: a sama dengan b"
else
  echo "$a -eq $b: a tidak sama dengan b"
fi
```
Output:   
```bash
15 -eq 7: a tidak sama dengan b
```

## 1.8 Conditional Statements
**Conditional statements** digunakan untuk memungkinkan program dapat membuat keputusan yang benar dengan memilih tindakan tertentu berdasarkan syarat/kondisi tertentu.
Ada 2 jenis conditional statements dalam Unix shell, yaitu:
1. **if...else**
2. **case**
  
### 1.8.1 If...Else
Syntax:
```bash
if [ kondisi1 ]
then 
  perintah1 
elif [ kondisi2 ]
then
  perintah2 
else
  alternatif_perintah
fi
```
Contoh:
```bash
#!/bin/bash

cintaku=100
cintanya=88

if [ $cintaku == $cintanya ]
then
  echo "cintaku sama dengan cintanya"
elif [ $cintaku -gt $cintanya ]
then
  echo "cintaku lebih besar dari cintanya"
elif [ $a -lt $cintanya ]
then
  echo "cintaku lebih kecil dari cintanya"
else
  echo "Tidak ada kondisi yang memenuhi"
fi
```
Output:
```bash
cintaku lebih besar dari cintanya
```

### 1.8.2 Case
Syntax:
```bash
case var in
  pola1)
    perintah1 
    ;;
  pola2)
    perintah2 
    ;;
  *)
    alternatif_perintah
    ;;
esac
```
Contoh:
```bash
#!/bin/bash

echo "Aku udah suka sama kamu dari lama, kamu mau ga jadi pacar aku?"
echo "1. Ya"
echo "2. Tidak"
echo "3. Aku gak bisa jawab sekarang"
echo -n "jawab: "
read jawaban

case "$jawaban" in
  "1")
    echo "Ga ada hal yang lebih aku tunggu dari ini, terimakasih!!!"
    ;;
  "2")
    echo "Oke, maaf ya udah ganggu waktu kamu"
    ;;
  "3")
    echo "Gantung aja aku, gantung aja!!!"
    ;;
  *)
    echo "Apa apa? Gimana??"
    ;;
esac
```
Output:   
![hasil-case](/gambar/hasil-case.png)

## 1.9 Loop
**Loop** digunakan untuk mengeksekusi serangkaian perintah berulang kali. Ada beberapa macam shell loops:
  1. While loop
  2. For loop
  3. Until loop
  4. Select loop

### 1.9.1 While loop
**While loop** digunakan untuk mengeksekusi serangkaian perintah berulang kali **selama** suatu kondisi terpenuhi. While digunakan jika kita ingin memanipulasi suatu variabel secara berulang-ulang.
Syntax:
```bash
while kondisi
do
  perintah 
done
```
Contoh:
```bash
#!/bin/bash

a=0

while [ $a -lt 10 ]
do
echo $a
  a=$((a + 2))
done
```
Output:
```bash
0
2
4
6
8
```
### 1.9.2 For loop
**For loop** digunakan untuk mengulang serangkaian perintah untuk setiap item pada daftar.
Syntax:
```bash
for var in daftar_item
do
  perintah 
done
```
Contoh:
```bash
#!/bin/bash

for num in 1 2 3 4 5
do
  echo $num
done
```
Selain itu, bisa ditulis seperti ini:
```bash
#!/bin/bash

for ((num=1; num<=5; num=num+1))
do
  echo $num
done
```
Output:
```bash
1
2
3
4
5
```

### 1.9.3 Until loop
Berbeda dengan while, **until loop** digunakan untuk mengeksekusi serangkaian perintah berulang kali **sampai** suatu kondisi terpenuhi.
Syntax:
```bash
until kondisi
do
  perintah
done
```
Contoh:
```bash
#!/bin/bash

a=0

until [ ! $a -lt 10 ]
do
  echo $a
  a=$((a + 2))
done
```
Output:
```bash
0
2
4
6
8
```

### 1.9.4 Select loop
**Select loop** digunakan ketika kita ingin membuat sebuah program dengan beberapa daftar pilihan yang bisa dipilih oleh user, misalnya daftar menu.
Syntax:
```bash
select var in daftar_item
do
  perintah
done
```
Contoh:
```bash
#!/bin/bash

select minuman in teh kopi air jus susu semua gaada
do
  case $minuman in
    teh|kopi|air|semua)
      echo "Maaf, habis"
      ;;
    jus|susu)
      echo "Tersedia"
    ;;
    gaada)
      break
    ;;
    *) echo "Tidak ada di daftar menu"
    ;;
  esac
done
```
Output:   
![hasil-select-loop](/gambar/hasil-select-loop.png)

### 1.9.5 Nesting Loops
Semua jenis loop di atas mendukung konsep nesting, artinya kita dapat menempatkan satu loop ke dalam loop lain, baik loop yang sejenis maupun berbeda jenis
Contoh:
```bash
#!/bin/sh

a=0

while [ "$a" -lt 10 ]  #loop1
do
  b="$a"
  while [ "$b" -ge 0 ]  #loop2
  do
    echo -n "$b "
    b=`expr $b - 1`
  done
  echo ""
  a=`expr $a + 1`
done
```
Output:
```bash
0
1 0
2 1 0
3 2 1 0
4 3 2 1 0
5 4 3 2 1 0
6 5 4 3 2 1 0
7 6 5 4 3 2 1 0
8 7 6 5 4 3 2 1 0
9 8 7 6 5 4 3 2 1 0
```
## 1.10 Function
**Fungsi** digunakan untuk memecah fungsionalitas keseluruhan script menjadi sub-bagian yang lebih kecil. Sub-bagian itu dapat dipanggil untuk melakukan tugas masing-masing apabila diperlukan.
Syntax:
```bash
nama_fungsi () { 
  perintah1
  perintah2
  ...
  perintahN
}
```
Contoh:
```bash
#!/bin/bash
#define functions
ask_name() {
  echo "Siapa namamu?"
}
reply() {
  read nama
  echo "Hai $nama, selamat datang di materi camin AJK!"  
}

#call functions
ask_name
reply
```
Output:   
![hasil-fungsi](/gambar/hasil-fungsi.png)

### 1.10.1 Nested Functions
Sama halnya dengan loop, function juga bisa menerapkan konsep nested. Dimana kita bisa memanggil sebuah fungsi di dalam fungsi.
```bash
#!/bin/bash

#define functions
ask_name() {
  echo "Siapa namamu?"
  reply   #call reply function inside ask_name function
}
reply() {
  read nama
  echo "Hai $nama, selamat datang di materi camin AJK!"
}

#call functions
ask_name
```
Output:   
![hasil-fungsi](/gambar/hasil-fungsi-nested.png)


## Referensi
* Modul 1 Mata Kuliah Sistem Operasi TC 2020
* [https://www.tutorialspoint.com/unix/shell_scripting.htm](https://www.tutorialspoint.com/unix/shell_scripting.htm)
* [https://pemula.linux.or.id/programming/bash-shell.html](https://pemula.linux.or.id/programming/bash-shell.html)
* [https://www.codepolitan.com/belajar-bash-mencoba-bash-untuk-pertama-kali-57bbca3c28e54-17341](https://www.codepolitan.com/belajar-bash-mencoba-bash-untuk-pertama-kali-57bbca3c28e54-17341)
* [https://pemula.linux.or.id/programming/bash-shell.html](https://pemula.linux.or.id/programming/bash-shell.html)
