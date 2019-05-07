---
permalink: /offensive/recon/
title: "Reconnaissance"
layout: single
excerpt: " "
author_profile: true
toc: true
toc_label: "Reconnaissance TOC"
toc_icon: "laptop"
---

## Overview
This section will cover the basics of engagement reconnaissance. 

## Search Engines

### People Search
* [Pipl](https://pipl.com/)

### Computer Search
* [Censys.io](https://censys.io/)
* [Shodan](https://www.shodan.io/)
* [BinaryEdge](https://app.binaryedge.io/services/query)

### Whois Registries
* Europe - [RIPE](http://www.ripe.net/)
* Latin America - [LACNIC](http://www.lacnic.net/en/)
* North America - [ARIN](https://www.arin.net/)
* Asia - [APNIC](http://www.apnic.net/)
* Africa - [AFRINIC](http://www.afrinic.net/)

### Domain Reputation
* [McAfee](https://trustedsource.org/en/feedback/url?action=checksingle)
* [Fortiguard](https://fortiguard.com/webfilter)
* [Bluecoat and Symantec](http://sitereview.bluecoat.com/)

# Mailserver Query
* [MXToolbox](https://mxtoolbox.com/)

## Network Scanning
### Nmap
Generate a list of IP Address from list of CIDR
```
nmap -sL -iL <file of targets> -oA <output filename>
```

Basic SYN Stealth port scan
```
nmap -sS --open -iL <file of targets> -oA <output filename>
```

Cut up nmap file. Useful to trim down target list of only identified online hosts. 
```
cat nmap_file.gnmap|cut -d' ' -f2| cut -d' ' -f2| sort| uniq| grep -v Nmap > online_targets.txt
```

Scanning only Top 100 ports
```
nmap --top-ports 100 --open -iL <file of targets> -oA <output filename>
```

Aggressive port scan (Enable OS detection, version detection, script scanning, and traceroute)
```
nmap -A --open -iL <file of targets> -oA <output filename>
```

Run an NSE script
```
nmap --script=dns-brute -iL <file of targets> -oA <output filename>
```
Run SMB Scan
```
nmap --script=smb-enum-shares -p445
```

Parse out certain ports of an nmap scan
```
cat nmap_slow_common_pri.gnmap |grep -e "80/open" -e "443/open"|cut -d" " -f2 > targets_web.txt
```

### Masscan
Basic scan
```
masscan 0.0.0.0/4 -p80 --rate 10000
```

## Domain Enumeration
### DNSRecon
DNS Reverse lookup

Normal dns reverse lookup of IP range with CSV output
```
dnsrecon -t rvl -r <target CIDR range> -c output.csv
```

Perform default enumeration of a domain
```
dnsrecon -d <domain>
```

Perform zone transfer attempt
```
dnsrecon -t axfr -d <domain>
```

### The Harvester
Collect domain information, subdomain, user emails, and other information from public resources. 
```
theHarvester -d site.org -b all
```

### Metagoofil
Collect files from a website such as PDF, DOC, and other common office documents. It will scrape them for metadata and generate a report.
```
metagoofil -d <target>.com -t pdf,doc,xls,ppt,odp,ods,docx,xlsx,pptx -l 200 -n 5 -o /tmp/metagoofil/ -f /tmp/metagoofil/result.html
``` 

## Wireless Enumeration
List out detailed information about wireless APs
```
iwlist wlan0 scanning
```

List out APs and clients connected to them
```
airmon-ng start wlan0
```

## Tools
### Multi Use Tools
* [ViewDNS](https://viewdns.info/)