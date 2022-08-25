# Hunting XSS di Search Bar

>Kalau menemukan form search bar
> 1. Masukin random string, misalnya test (Analisa hasil input ini munculnya dimana, apakah didalam tag html, apakah didalam tag script, apakah didalemnya html comment, dll) 
> 2. Masukin special chara, khususnya ' " > < = 
> 
> Kalau muncul diluar tag `<script>`
> 1. Analisa inputnya muncul dimana, kalau didalam atribut tinggal di escape pakai "> atau kalau didalam html comment tinggal di escape pakai —> 
> 2. Terus coba tes beberapa tag html, apakah ada filter kayak `<svg>`, `<iframe>`, `<img>`,` <src>` 
> 3. Kalau bisa lagi, coba test masukin events js, kayak onclick, onload, onerror, dll 
> 4. Nah kalau bisa lagi tinggal masukin alert / prompt / confirm / print
> 5. Done
>    
>  Kalau muncul didalam tag `<script>`
>  1. Kalau memang bisa masukin special chara kayak " ' } ), gimana caranya nge "escape" dari kondisi if / variable / fungsi js terus tambahin fungsi js kek alert(1) 
>  2. Atau ditutup langsung pakai `</script>` terus diikuti payloadnya 
>  3. Done


by : @daffainfo

Cek juga [AllAboutBugBounty](https://github.com/daffainfo/AllAboutBugBounty)
