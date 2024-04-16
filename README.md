# netbox-ip-status
Show when an IP address was last seen, and its actual reverse DNS record in Netbox

Copy config.py.sample to config.py and edit as appropriate.
This script needs to run with root privileges for its ping functionality.

Run on a cronjob once a day.

## Dependencies

It is necessary that the netbox system have the following tags:

- ipstatus
- found
- lastseen:today
- lastseen:yesterday
- lastseen:week
- lastseen:month
- lastseen:year
- lastseen:overayear
- lastseen:never

for simplicity, import the contents of the netbox_ip_status_tags.csv file into netbox-url/extras/tags/import/#tab_import-form

### installing dependencies

```sh
virtualenv venv
source venv/bin/activate
pip install -r requirements.txt
```


## principle of operation

Set the `ipstatus` tag on the networks you plan to scan.


```sh
# manual script launch
sudo /path/to/venv/bin/python netbox_ip_status.py
```

