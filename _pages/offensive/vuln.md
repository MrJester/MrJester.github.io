---
permalink: /offensive/vuln/
title: "Vulnerability Modeling"
layout: single
excerpt: " "
author_profile: true
toc: true
toc_label: "Vuln Modeling TOC"
toc_icon: "laptop"
---

## Overview
This section will cover the basics of vulnerability modeling of targets. 

## Vulmap
Vulmap tool will scan the local host to identify local vulnerabilities that could be exploited.

Vulmap - https://github.com/vulmon/Vulmap
```
python vulmap.py
```

## Nmap
Nmap NSE scripts can be used to identify vulnerabilities on hosts
```
nmap -p <port> --script=*cve*.nse <target> -oa nmap-vuln-scan
```
```
nmap --script=vulners.nse <target> -oa nmap-vulners-scan
```


