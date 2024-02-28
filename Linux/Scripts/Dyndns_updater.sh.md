Put this file update.sh in a folder /home/nick/dyndns/
	There  maybe be a file ips.txt generated

```bash
#!/bin/bash
#This is secret so don't share online
#################### CHANGE THE FOLLOWING VARIABLES ####################
TOKEN="715b8520f953af41a10a3e9cffa43215ebbabf2823addafa26f84acb919bd2ea"
DOMAIN="ndpost.me"
RECORD_ID="ndpost.me"
LOG_FILE="/home/nick/dyndns/ips.txt"
########################################################################

CURRENT_IPV4="$(dig +short myip.opendns.com @resolver1.opendns.com)"
LAST_IPV4="$(tail -1 $LOG_FILE | awk -F, '{print $2}')"

if [ "$CURRENT_IPV4" = "$LAST_IPV4" ]; then
    echo "IP has not changed ($CURRENT_IPV4)"
else
    echo "IP has changed: $CURRENT_IPV4"
    echo "$(date),$CURRENT_IPV4" >> "$LOG_FILE"
    curl -X PUT -H "Content-Type: application/json" -H "Authorization: Bearer $TOKEN" -d '{"data":"'"$CURRENT_IPV4"'"}' "https://api.digitalocean.com/v2/domains/$DOMAIN/records/$RECORD_ID"
fi
```
