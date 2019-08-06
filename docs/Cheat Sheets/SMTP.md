---
tags: [smtp]
---
# SMTP

## SMTP user enumeration

If a SMTP server is misconfigured some command may be available:

- `VRFY` - ask server to verify an email address
- `EXPN` - ask server the membership of a mailing list

Tools: nc, script, metasploit (`auxiliary/scanner/smtp/smtp_enum`)

MSF description:

> The SMTP service has two internal commands that allow the enumeration of users: VRFY (confirming the names of valid users) and EXPN (which reveals the actual address of users aliases and lists of e-mail (mailing lists)). Through the implementation of these SMTP commands can reveal a list of valid users.
