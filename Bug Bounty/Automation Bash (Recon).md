# Automation Bash for Recon
---
Tujuan dari automation bash ada menjalankan satu perintah/command pada terminal untuk menjalankan beberapa perintah

> Notes :
> save di `.zshrc` atau `.bashrc`


#### Search Subdomain from crt.sh
```bash
crtsh(){
    curl -s https://crt.sh/?q=%25.$1 | grep ">*.$1" | sed 's/<[/]*[TB][DR]>/\n/g' | grep -vE "<|^[\*]*[\.]*$1" | sort -u | awk 'NF'
}
```

#### Search Subdomain from crt.sh + httprobe
```bash
crtprobe(){
    curl -s https://crt.sh/\?q\=\%.$1\&output\=json | jq -r '.[].name_value' | sed 's/\*\.//g' | sort -u | httprobe | tee alive.txt
}
```