# FFuF
Directory Fuzzing / Brute Force
[Learn More](https://codingo.io/tools/ffuf/bounty/2020/09/17/everything-you-need-to-know-about-ffuf.html)

### Normal Usage
```bash
$ ffuf -w <wordlist> -u http://<TARGET>/FUZZ
```


#### Additionals
- `-t 60` : set threads ke 60
- `-rate 20` : membuat rate request menjadi 20req/second
- `-mc 200,301,403` : mencocokkan status code seperti yang diinginkan
- `-fc 403,404,405` : melakukan filtering status code agar tidak ditampilkan
- `-fs 12312` : melakukan filtering response size agar tidak ditampilkan
- `-o out` : output dari ffuf
