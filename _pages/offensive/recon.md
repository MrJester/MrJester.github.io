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

### Whois Registries
* Europe - [RIPE](http://www.ripe.net/)
* Latin America - [LACNIC](http://www.lacnic.net/en/)
* North America - [ARIN](https://www.arin.net/)
* Asia - [APNIC](http://www.apnic.net/)
* Africa - [AFRINIC](http://www.afrinic.net/)

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

### Masscan
Basic scan
```
masscan 0.0.0.0/4 -p80 --rate 10000
```

## Domain Enumeration
### The Harvester
```
theHarvester -d site.org -b all
```

## Tools
* [ViewDNS](https://viewdns.info/)