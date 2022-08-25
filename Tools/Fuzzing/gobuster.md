# Gobuster
Directory Fuzzing

### Normal Usage
```bash
$ gobuster dir -u http://<web or ip machine> -w <wordlist location>
```


#### Additionals
- `-t 60` : threads sebanyak 60
- `-o out` : output file
- `-q` : quite (no banner and other)
- `-x php,html,etc` : ==file extension==
- `-s 200,301,403,etc` : spesifik ==status kode== yang diiinginkan
