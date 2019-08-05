---
tags: [osint]
---
# theHarvester

## References

Multi-purpose information gathering tool: emails, names, subdomains, IPs, URLs.

- https://github.com/laramies/theHarvester
- https://inventory.rawsec.ml/tools.html#theHarvester

## Example of command and options

Specify a domain and a source to find IPs, sub-domains and emails:

```
theharvester -d cisco.com -b google
```

Available sources:

```
baidu, bing, bingapi, censys, crtsh, cymon,
dnsdumpster, dogpile, duckduckgo, google, google-
certificates, hunter, intelx, linkedin, netcraft,
securityTrails, threatcrowd, trello, twitter, vhost,
virustotal, yahoo, all
```
