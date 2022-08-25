# Dorking
---
### Google
---
1. Mencari Open Redirect
`site:redirect.com inurl:returnURL`

2. Mencari SQL Error (Lead to SQLi)
`site:x intext:"sql syntax near" | intext:"syntax error has occurred" | intext:"incorrect syntax near" | intext:"unexpected end of SQL command" | intext:"Warning: mysql_connect()" | intext:"Warning: mysql_query()" | intext:"Warning: pg_connect()"`


### Shodan
---
1. Mencari berdasarkan [Favicon](https://github.com/sansatart/scrapts/blob/master/shodan-favicon-hashes.csv)
`http.favicon.hash:494866796`

2. Mencari Dashboard Jenkins
`http.component:"jenkins" ssl:"target"`  OR  `html:"Dashboard Jenkins" ssl:"target"` (atau bisa diubah ssl menjadi org)