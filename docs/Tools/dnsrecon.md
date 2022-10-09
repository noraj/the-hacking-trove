---
tags: [osint,dns]
---
# DNSRecon

## References

DNS reconnaissance tool: AXFR, DNS records enumeration, TLD expansion, wildcard resolution, subdomain bruteforce, PTR record lookup, check for cached records.

- https://github.com/darkoperator/dnsrecon
- https://inventory.raw.pm/tools.html#DNSRecon

## Example of execution

Trying AXFR enum:

```
$ dnsrecon -d megacorpone.com -t axfr
[*] Testing NS Servers for Zone Transfer
[*] Checking for Zone Transfer for megacorpone.com name servers
[*] Resolving SOA Record
[+]      SOA ns1.megacorpone.com 38.100.193.70
[*] Resolving NS Records
[*] NS Servers found:
[*]     NS ns3.megacorpone.com 38.100.193.90
[*]     NS ns1.megacorpone.com 38.100.193.70
[*]     NS ns2.megacorpone.com 38.100.193.80
[*] Removing any duplicate NS server IP Addresses...
[*]  
[*] Trying NS server 38.100.193.90
[+] 38.100.193.90 Has port 53 TCP Open
[-] Zone Transfer Failed!
[-] Zone transfer error: REFUSED
[*]  
[*] Trying NS server 38.100.193.80
[+] 38.100.193.80 Has port 53 TCP Open
[+] Zone Transfer was successful!!
[*]      NS ns1.megacorpone.com 38.100.193.70
[*]      NS ns2.megacorpone.com 38.100.193.80
[*]      NS ns3.megacorpone.com 38.100.193.90
[*]      MX @.megacorpone.com fb.mail.gandi.net 217.70.178.217
[*]      MX @.megacorpone.com fb.mail.gandi.net 217.70.178.216
[*]      MX @.megacorpone.com fb.mail.gandi.net 217.70.178.215
[*]      MX @.megacorpone.com spool.mail.gandi.net 217.70.178.1
[*]      A admin.megacorpone.com 38.100.193.83
[*]      A beta.megacorpone.com 38.100.193.88
[*]      A fs1.megacorpone.com 38.100.193.82
[*]      A intranet.megacorpone.com 38.100.193.87
[*]      A mail.megacorpone.com 38.100.193.84
[*]      A mail2.megacorpone.com 38.100.193.73
[*]      A ns1.megacorpone.com 38.100.193.70
[*]      A ns2.megacorpone.com 38.100.193.80
[*]      A ns3.megacorpone.com 38.100.193.90
[*]      A router.megacorpone.com 38.100.193.71
[*]      A siem.megacorpone.com 38.100.193.89
[*]      A snmp.megacorpone.com 38.100.193.85
[*]      A support.megacorpone.com 173.246.47.170
[*]      A syslog.megacorpone.com 38.100.193.66
[*]      A test.megacorpone.com 38.100.193.67
[*]      A vpn.megacorpone.com 38.100.193.77
[*]      A www.megacorpone.com 38.100.193.76
[*]      A www2.megacorpone.com 38.100.193.79
[*]  
[*] Trying NS server 38.100.193.70
[+] 38.100.193.70 Has port 53 TCP Open
[-] Zone Transfer Failed!
[-] Zone transfer error: REFUSED
```
