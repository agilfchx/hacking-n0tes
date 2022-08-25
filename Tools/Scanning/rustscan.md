# Nmap
Network Mapping

### Normal Usage
```bash
$ rustscan -a <ip address>
```


#### Additionals
- `-- -A -sCV` : menambahkan perintah nmap (tambah --)
- `-p 443` : mengscan satu port
- `-p 53,80,8080` : mengscan port tertentu
- `--range 1-1000` : mengscan dengan range tertentu
