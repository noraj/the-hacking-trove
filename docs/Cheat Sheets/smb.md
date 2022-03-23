---
tags: [smb,samba]
---
# Samba (SMB)

## Windows version mapping

- SMB1.0 – Windows 2000, XP and Windows 2003
- SMB2.0 – Windows Vista SP1 and Windows 2008
- SMB2.1 – Windows 7 and Windows 2008 R2
- SMB3.0 – Windows 8 and Windows 2012

## SMB NetBIOS

Listen on TCP ports **139** and **445**.

Get NetBIOS info: (other than with enum4linux).

```
$ nbtscan -r 10.0.0.1
```

## NSE scripts

```
$ ls -1 /usr/share/nmap/scripts/smb*
/usr/share/nmap/scripts/smb2-capabilities.nse
/usr/share/nmap/scripts/smb2-security-mode.nse
/usr/share/nmap/scripts/smb2-time.nse
/usr/share/nmap/scripts/smb2-vuln-uptime.nse
/usr/share/nmap/scripts/smb-brute.nse
/usr/share/nmap/scripts/smb-double-pulsar-backdoor.nse
/usr/share/nmap/scripts/smb-enum-domains.nse
/usr/share/nmap/scripts/smb-enum-groups.nse
/usr/share/nmap/scripts/smb-enum-processes.nse
/usr/share/nmap/scripts/smb-enum-services.nse
/usr/share/nmap/scripts/smb-enum-sessions.nse
/usr/share/nmap/scripts/smb-enum-shares.nse
/usr/share/nmap/scripts/smb-enum-users.nse
/usr/share/nmap/scripts/smb-flood.nse
/usr/share/nmap/scripts/smb-ls.nse
/usr/share/nmap/scripts/smb-mbenum.nse
/usr/share/nmap/scripts/smb-os-discovery.nse
/usr/share/nmap/scripts/smb-print-text.nse
/usr/share/nmap/scripts/smb-protocols.nse
/usr/share/nmap/scripts/smb-psexec.nse
/usr/share/nmap/scripts/smb-security-mode.nse
/usr/share/nmap/scripts/smb-server-stats.nse
/usr/share/nmap/scripts/smb-system-info.nse
/usr/share/nmap/scripts/smb-vuln-conficker.nse
/usr/share/nmap/scripts/smb-vuln-cve2009-3103.nse
/usr/share/nmap/scripts/smb-vuln-cve-2017-7494.nse
/usr/share/nmap/scripts/smb-vuln-ms06-025.nse
/usr/share/nmap/scripts/smb-vuln-ms07-029.nse
/usr/share/nmap/scripts/smb-vuln-ms08-067.nse
/usr/share/nmap/scripts/smb-vuln-ms10-054.nse
/usr/share/nmap/scripts/smb-vuln-ms10-061.nse
/usr/share/nmap/scripts/smb-vuln-ms17-010.nse
/usr/share/nmap/scripts/smb-vuln-regsvc-dos.nse
```

Example: `nmap -v -p 139, 445 --script=smb-os-discovery 10.0.0.1`
