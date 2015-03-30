Trier les user agents depuis les logs :
````bash
cat nginx.log |  cut -d"\"" -f6 | sort | uniq -c  | sort -rn
````
