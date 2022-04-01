# regex-for-hacking
Regex for hack

## TheHarvester Grep E-mail
cat theharvester.xml | grep -oP '(?<=<email>).*?(?=</email>)'

## TheHarvester grep Hostname

cat theharvester.xml | grep -oP '(?<=<hostname>).*?(?=</hostname>)'

## TheHarvester grep IP

cat theharvester.xml | grep -oP '(?<=<ip>).*?(?=</ip>)' | tr , '\n' | tr -d " "
