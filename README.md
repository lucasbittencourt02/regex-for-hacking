# regex-for-hacking
Some greps to extract information from hacking tools
## TheHarvester Grep E-mail
```
cat theharvester.xml | grep -oP '(?<=<email>).*?(?=</email>)'
```
## TheHarvester grep Hostname
```
cat theharvester.xml | grep -oP '(?<=<hostname>).*?(?=</hostname>)'
```
## TheHarvester grep IP
```
cat theharvester.xml | grep -oP '(?<=<ip>).*?(?=</ip>)' | tr , '\n' | tr -d " "
```
## DNSEnum grep IP
```
cat dnsenum.xml | grep -oP '(?<=<host>).*?(?=</host>)' | awk -F '<' '{print $1}'
```
## DNSEnum grep hostname
```
cat lidercap_dnsenum | grep -oP '(?<=<hostname>).*?(?=</hostname>)'
```
### Grep to get subdomains from Hakrawler
```
sed -e '/[A-Z]/d' -e '/*/d' [LIST-FROM-HAKRAWLER] | grep -oP '[a-z0-9]+\.[a-z]+\.[a-z]+' | sort -u
```
### Grep IPs Up from NMAP
```
sudo nmap -sP 172.16.12.0/24 -oG - | awk '/Up$/{print $2}'
```
### Grep IPs from ifconfig and than validating a http and https are up
```
ip -o addr show | grep -v 'inet6' | awk '/wlan0/ {print $4}' | anew network_local | sudo nmap -sP -iL network_local -oG - | awk '/Up$/{print $2}' | httprobe
```
### Grep IPs Port 445 are up

```
sudo nmap -Pn -n -p 445 172.16.11.0/24 -oG - | awk '/445\/open/ {print $2}' 
```
### Grep Open Ports 

```
naabu --passive | grep ':' | sed 's/.*://' | anew ports.txt
```
### Grep and cut URLS paths
```
grep -oP 'https?://[^/]+(/\S*)' urls.txt | cut -d '/' -f 2
```
### Grep to remove extensions and params
```
grep -vE '\.(json|css|jpg|png|html|xml|pdf|gff|txt|js)$' urls.txt | urls.txt | sed 's/[?].*//' > filtradas.txt
```
