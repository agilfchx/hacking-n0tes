# Nmap
Network Mapping

### Normal Usage
```bash
$ nmap <ip address>
```


#### Additionals
- `-sV` : cek service version
- `-sC` : menjalankan script default yang digunakan nmap
- `-sU` : UDP Scan
- `--script=<name script>` : menggunakan script yang berada pada nmap (Lokasi script : ==/usr/share/nmap/scripts==)
- `-p 22` : scan pada port 22 (satu port saja)
- `-p-400` : scan mulai dari awal hingga 400
- `-p-` : scan semua port
- `-p http,https,etc` : scan hanya services tertentu
- `-Pn` : memperlakukan setiap host sebagai online 
- `-O` : OS Detection
- `-T4` : ==mantap pokoknya==
