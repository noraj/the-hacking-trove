---
tags: [osint]
---
# Google dorks

## Basic

Domain related search:

```
site:example.org
```

Excluding sub domains:

```
site:example.org -site:www.example.org
```

Example of search in title, in URL and exclude a file type:

```
intitle:"netbotz appliance" "OK" -filetype:pdf
intitle:"SpeedStream Router Management Interface"
inurl:"level/15/exec/-/show"
"# -FrontPage-" filetype:pwd inurl:(services|authors|administrators|users)
```

## GHDB

[Google Hacking Database](https://www.exploit-db.com/google-hacking-database)
