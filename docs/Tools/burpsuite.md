---
tags: [java,web,http]
---
# Burp Suite

=== Info
- **Description**: Intercepting proxy to replay, inject, scan and fuzz HTTP requests (a limited free version exists)
- Version tested: Professional v2022.9.6
- Review date: 20/11/2022
- [Website](https://portswigger.net/burp/)
- [Rawsec Inventory](https://inventory.raw.pm/tools.html#Burp%20Suite)
===

## Adding CA certificate to Linux system

[Adding CA certificate to web browsers](https://portswigger.net/burp/documentation/desktop/external-browser-config/certificate) is quite well documented. But what if you want to use other HTTP tools on a Linux system with Burp Suite?

We are not going to be able to intercept HTTPS with Burp Suite without importing Burp CA certificate.

In ArchLinux [Certificates authorities](https://wiki.archlinux.org/title/Transport_Layer_Security#Certificate_authorities) can be added like to system truststore that:

```
$ wget http://127.0.0.1:8080/cert
$ sudo trust anchor cert
```

Let's verify the CA was imported:

```
$ trust list | head -5
pkcs11:id=%3E%8E%2A%21%8B%B3%82%56%83%8D%04%2A%8D%3E%FD%5A%05%D1%7C%B4;type=cert
    type: certificate
    label: PortSwigger CA
    trust: anchor
    category: authority
```

