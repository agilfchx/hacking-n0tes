# SMB Shares Tools


### SMBMap
enumerate users samba share drives

```bash
$ smbmap -H <ip machine>
```

### SMBClient
enumerate users seperti **smbmap** 

```bash
$ smbclient -L \\<ip machine>
```

access directory i.e *anonymous* (no password)
```bash
$ smbclient \\\\<ip machine>\\anonymous
```

access using user
```bash
$ smbclient -U <user> \\\\<ip machine>\\<user>
```