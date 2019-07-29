---
tags: [dns]
---
# dig / drill

## References

man pages:

- dig: https://linux.die.net/man/1/dig
- drill: https://linux.die.net/man/1/drill

## Examples of execution

Get name servers (NS record):

```
$ drill NS megacorpone.com
;; ->>HEADER<<- opcode: QUERY, rcode: NOERROR, id: 44202
;; flags: qr rd ra ; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 0 
;; QUESTION SECTION:
;; megacorpone.com.     IN      NS

;; ANSWER SECTION:
megacorpone.com.        172800  IN      NS      ns1.megacorpone.com.
megacorpone.com.        172800  IN      NS      ns3.megacorpone.com.
megacorpone.com.        172800  IN      NS      ns2.megacorpone.com.

;; AUTHORITY SECTION:

;; ADDITIONAL SECTION:

;; Query time: 145 msec
;; SERVER: 192.168.1.254
;; WHEN: Thu May  2 17:00:07 2019
;; MSG SIZE  rcvd: 87


$ dig NS megacorpone.com   

; <<>> DiG 9.14.1 <<>> NS megacorpone.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 47373
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;megacorpone.com.               IN      NS

;; ANSWER SECTION:
megacorpone.com.        172800  IN      NS      ns2.megacorpone.com.
megacorpone.com.        172800  IN      NS      ns1.megacorpone.com.
megacorpone.com.        172800  IN      NS      ns3.megacorpone.com.

;; Query time: 146 msec
;; SERVER: 192.168.1.254#53(192.168.1.254)
;; WHEN: jeu. mai 02 16:59:53 CEST 2019
;; MSG SIZE  rcvd: 98
```

Get mail servers (MX record):

```
$ drill MX megacorpone.com
;; ->>HEADER<<- opcode: QUERY, rcode: NOERROR, id: 18651
;; flags: qr rd ra ; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 0 
;; QUESTION SECTION:
;; megacorpone.com.     IN      MX

;; ANSWER SECTION:
megacorpone.com.        86400   IN      MX      60 mail2.megacorpone.com.
megacorpone.com.        86400   IN      MX      10 fb.mail.gandi.net.
megacorpone.com.        86400   IN      MX      20 spool.mail.gandi.net.
megacorpone.com.        86400   IN      MX      50 mail.megacorpone.com.

;; AUTHORITY SECTION:

;; ADDITIONAL SECTION:

;; Query time: 142 msec
;; SERVER: 2001:861:3dc4:5e00:faab:5ff:fe14:bddc
;; WHEN: Thu May  2 17:00:26 2019
;; MSG SIZE  rcvd: 131

$ dig MX megacorpone.com

; <<>> DiG 9.14.1 <<>> MX megacorpone.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 21557
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;megacorpone.com.               IN      MX

;; ANSWER SECTION:
megacorpone.com.        259195  IN      MX      10 fb.mail.gandi.net.
megacorpone.com.        259195  IN      MX      20 spool.mail.gandi.net.
megacorpone.com.        259195  IN      MX      50 mail.megacorpone.com.
megacorpone.com.        259195  IN      MX      60 mail2.megacorpone.com.

;; Query time: 24 msec
;; SERVER: 192.168.1.254#53(192.168.1.254)
;; WHEN: jeu. mai 02 17:00:31 CEST 2019
;; MSG SIZE  rcvd: 142
```

Check AXFR to find sub-domains:

```bash
#!/bin/bash
domain='megacorpone.com'
ns=$(dig +noall +answer NS $domain | awk '{print $5}')
for server in $ns
do
  dig @$server AXFR $domain
done
```

Ref + video demo: https://gist.github.com/noraj/d4af1b1e7ab869abb4a71f0698f55695
