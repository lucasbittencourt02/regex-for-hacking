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
