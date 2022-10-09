---
tags: [osint,dns]
---
# DNSenum

## References

DNS reconnaissance tool: AXFR, DNS records enumeration, subdomain bruteforce, range reverse lookup.

- https://github.com/fwaeytens/dnsenum
- https://inventory.raw.pm/tools.html#dnsenum

## Example of execution

Find NS, MX and try zone transfer:

```
$ dnsenum megacorpone.com
Smartmatch is experimental at /usr/bin/dnsenum line 698.
Smartmatch is experimental at /usr/bin/dnsenum line 698.
dnsenum.pl VERSION:1.2.4

-----   megacorpone.com   -----


Host's addresses:
__________________



Name Servers:
______________

ns1.megacorpone.com.                     86400    IN    A        38.100.193.70
ns2.megacorpone.com.                     86400    IN    A        38.100.193.80
ns3.megacorpone.com.                     86400    IN    A        38.100.193.90


Mail (MX) Servers:
___________________

fb.mail.gandi.net.                       60       IN    A        217.70.178.217
fb.mail.gandi.net.                       60       IN    A        217.70.178.215
fb.mail.gandi.net.                       60       IN    A        217.70.178.216
spool.mail.gandi.net.                    24       IN    A        217.70.178.1
mail.megacorpone.com.                    86400    IN    A        38.100.193.84
mail2.megacorpone.com.                   86400    IN    A        38.100.193.73


Trying Zone Transfers and getting Bind Versions:
_________________________________________________


Trying Zone Transfer for megacorpone.com on ns1.megacorpone.com ... 
AXFR record query failed: REFUSED

Trying Zone Transfer for megacorpone.com on ns2.megacorpone.com ... 
megacorpone.com.                         259200   IN    SOA               (
megacorpone.com.                         259200   IN    MX               10
megacorpone.com.                         259200   IN    MX               20
megacorpone.com.                         259200   IN    MX               50
megacorpone.com.                         259200   IN    MX               60
megacorpone.com.                         259200   IN    NS       ns1.megacorpone.com.
megacorpone.com.                         259200   IN    NS       ns2.megacorpone.com.
megacorpone.com.                         259200   IN    NS       ns3.megacorpone.com.
admin.megacorpone.com.                   259200   IN    A        38.100.193.83
beta.megacorpone.com.                    259200   IN    A        38.100.193.88
fs1.megacorpone.com.                     259200   IN    A        38.100.193.82
intranet.megacorpone.com.                259200   IN    A        38.100.193.87
mail.megacorpone.com.                    259200   IN    A        38.100.193.84
mail2.megacorpone.com.                   259200   IN    A        38.100.193.73
ns1.megacorpone.com.                     259200   IN    A        38.100.193.70
ns2.megacorpone.com.                     259200   IN    A        38.100.193.80
ns3.megacorpone.com.                     259200   IN    A        38.100.193.90
router.megacorpone.com.                  259200   IN    A        38.100.193.71
siem.megacorpone.com.                    259200   IN    A        38.100.193.89
snmp.megacorpone.com.                    259200   IN    A        38.100.193.85
support.megacorpone.com.                 259200   IN    A        173.246.47.170
syslog.megacorpone.com.                  259200   IN    A        38.100.193.66
test.megacorpone.com.                    259200   IN    A        38.100.193.67
vpn.megacorpone.com.                     259200   IN    A        38.100.193.77
www.megacorpone.com.                     259200   IN    A        38.100.193.76
www2.megacorpone.com.                    259200   IN    A        38.100.193.79

Trying Zone Transfer for megacorpone.com on ns3.megacorpone.com ... 
AXFR record query failed: REFUSED

brute force file not specified, bay.
```
