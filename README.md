# regex-for-hacking
Regex for hack

## TheHarvester Grep E-mail
cat theharvester.xml | grep -oP '(?<=<email>).*?(?=</email>)'

## TheHarvester grep Hostname

cat theharvester.xml | grep -oP '(?<=<hostname>).*?(?=</hostname>)'

## TheHarvester grep IP

cat theharvester.xml | grep -oP '(?<=<ip>).*?(?=</ip>)' | tr , '\n' | tr -d " "

## DNSEnum grep IP
cat dnsenum.xml | grep -oP '(?<=<host>).*?(?=</host>)' | awk -F '<' '{print $1}'

## DNSEnum grep hostname
cat lidercap_dnsenum | grep -oP '(?<=<hostname>).*?(?=</hostname>)'
