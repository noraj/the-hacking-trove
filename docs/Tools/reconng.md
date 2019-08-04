---
tags: [osint]
---
# Recon-ng

## References

Web-based reconnaissance tool.

- https://bitbucket.org/LaNMaSteR53/recon-ng/
- https://inventory.rawsec.ml/tools.html#Recon-ng

## Examples of execution

Whois search email:

```
$ recon-ng
[recon-ng][default] > use recon/domains-contacts/whois_pocs
[recon-ng][default][whois_pocs] > set SOURCE orange.com
SOURCE => orange.com
[recon-ng][default][whois_pocs] > run

----------
ORANGE.COM
----------
[*] URL: http://whois.arin.net/rest/pocs;domain=orange.com
[*] URL: http://whois.arin.net/rest/poc/ABUSE3681-ARIN
...
```

Try to find vuln on Open Bug Bounty:

```
[recon-ng][default] > use recon/domains-vulnerabilities/xssposed
[recon-ng][default][xssposed] > set SOURCE orange.com
SOURCE => orange.com
[recon-ng][default][xssposed] > run

----------
ORANGE.COM
----------
[*] Category: XSS
[*] Example: https://www.orange.com
[*] Host: orange.com
[*] Publish_Date: 2017-09-27 12:36:50
[*] Reference: https://www.openbugbounty.org/reports/316983/
[*] Status: fixed
[*] --------------------------------------------------
...
```

Find sub-domains:

```
[recon-ng][default] > use recon/domains-hosts/google_site_web
[recon-ng][default][google_site_web] > set SOURCE orange.com
SOURCE => orange.com
[recon-ng][default][google_site_web] > run

----------
ORANGE.COM
----------
[*] Searching Google for: site:orange.com
[*] [host] www.orange.com (<blank>)
[*] [host] recargas.orange.com (<blank>)
...
```
