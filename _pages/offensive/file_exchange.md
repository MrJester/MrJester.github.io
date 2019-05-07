---
permalink: /offensive/file_exchange/
title: "Exchange Files"
layout: single
excerpt: " "
author_profile: true
toc: true
toc_label: "Exchange Files TOC"
toc_icon: "laptop"
---

## Overview
This section will be a list of commonly used techniques for exchanging files between hosts that I have had success using.

## Python
### python2:
This starts an HTTP service in the current directory with the port 1337
```
python -m SimpleHTTPServer 1337
```

### python3:
This starts an HTTP service in the current directory with the port 1337
```
python -m http.server 1337
```

## Twistd
This start an HTTP service in the current directory with port 1337
```
twistd -n web --port tcp:1337 --path .
```

## PHP
### PHP 5.4+
When the PHP version is greater than 5.4, you can use PHP to start the HTTP service in the
current directory, the port is 1337.
```
php -S 0.0.0.0:1337
```

## Ruby
### Ruby 1.9.2+
This start an HTTP service in the current directory with port 1337
```
ruby -run -e httpd . -p 1337
```

## Busybox
This start an HTTP service in the current directory with port 1337
```
busybox httpd -f -p 8000
```

## IIS Express
```
"C:\Program Files (x86)\IIS Express\iisexpress.exe" /path:C:\MyWeb /port:8000
```
