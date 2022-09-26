# FFuF
Directory Fuzzing / Brute Force
[Learn More](https://codingo.io/tools/ffuf/bounty/2020/09/17/everything-you-need-to-know-about-ffuf.html)

### Normal Usage
```bash
$ ffuf -w <wordlist> -u http://<TARGET>/FUZZ
```

### Brute Force Attacks
```bash
$ ffuf -u http://10.10.93.143/sqli-labs/Less-11/ -c -w /usr/share/seclists/Passwords/Leaked-Databases/hak5.txt -X POST -d 'uname=Dummy&passwd=FUZZ&submit=Submit' -fs 1435 -H 'Content-Type: application/x-www-form-urlencoded'`
```

### Fuzzing API endpoint
```bash
$ ffuf -u 'http://10.10.93.143/sqli-labs/Less-1/?FUZZ=1' -c -w /usr/share/seclists/Discovery/Web-Content/burp-parameter-names.txt -fw 39
```

### Fuzzing Values
```bash
$ for i in {0..255}; do echo $i; done | ffuf -u 'http://10.10.93.143/sqli-labs/Less-1/?id=FUZZ' -c -w - -fw 33

$ seq 0 255 | ffuf -u 'http://10.10.93.143/sqli-labs/Less-1/?id=FUZZ' -c -w - -fw 33

$ cook '[0-255]' | ffuf -u 'http://10.10.93.143/sqli-labs/Less-1/?id=FUZZ' -c -w - -fw 33
```


### Fuzzing Subdomains
```bash
$ ffuf -u http://FUZZ.mydomain.com -c -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt
```

#### Additionals
- `-t 60` : set threads ke 60
- `-rate 20` : membuat rate request menjadi 20req/second
- `-mc 200,301,403` : mencocokkan status code seperti yang diinginkan
- `-fc 403,404,405` : melakukan filtering status code agar tidak ditampilkan
- `-fs 12312` : melakukan filtering response size agar tidak ditampilkan
- `-of md -o ffuf.md` : save output ke markdown dgn nama ffuf.md
- `-ic` : ignore comments (seperti di wordlists *directory-list-2.3-medium.txt*)
- `-c` : colorize output
- `-v` : print full URL and redirect location
