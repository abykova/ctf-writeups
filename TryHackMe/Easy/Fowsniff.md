https://tryhackme.com/room/ctf

Fowsniff CTF

nmap -n <TARGET_IP>
nmap -sC -sV <TARGET_IP> -p 22,80,110,143

Using Google, can you find any public information about them?

see Hints 

cat fowsniff_userpass
cat fowsniff_userpass | awk -F ':' '{ print $2 }'

...
