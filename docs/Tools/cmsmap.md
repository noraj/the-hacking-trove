---
tags: [cms,web]
---
# CMSmap

## References

WordPress, Joomla, Drupal, Moodle CMS security scanner.

- https://github.com/Dionach/CMSmap
- https://inventory.rawsec.ml/tools.html#CMSmap

## Example of execution

```
python3 ~/CTF/tools/cmsmap/cmsmap.py http://10.0.0.1 -f D
[-] Date & Time: 15/06/2019 00:17:47
[I] Threads: 5
[-] Target: http://10.0.0.1 (10.0.0.1)
[M] Website Not in HTTPS: http://10.0.0.1
[I] Server: Microsoft-IIS/8.5
[L] X-Frame-Options: Not Enforced
[I] Strict-Transport-Security: Not Enforced
[I] X-Content-Security-Policy: Not Enforced
[I] X-Content-Type-Options: Not Enforced
[L] Robots.txt Found: http://10.0.0.1/robots.txt
[I] CMS Detection: Drupal
[I] Drupal Version: 7.28
[M]  EDB-ID: 46510 "Drupal < 8.5.11 / < 8.6.10 - RESTful Web Services unserialize() Remote Command Execution (Metasploit)"
[M]  EDB-ID: 44448 "Drupal < 8.3.9 / < 8.4.6 / < 8.5.1 - 'Drupalgeddon2' Remote Code Execution (PoC)"
[M]  EDB-ID: 44449 "Drupal < 7.58 / < 8.3.9 / < 8.4.6 / < 8.5.1 - 'Drupalgeddon2' Remote Code Execution"
[M]  EDB-ID: 44482 "Drupal < 8.3.9 / < 8.4.6 / < 8.5.1 - 'Drupalgeddon2' Remote Code Execution (Metasploit)"
[M]  EDB-ID: 44542 "Drupal < 7.58 - 'Drupalgeddon3' (Authenticated) Remote Code Execution (PoC)"
[M]  EDB-ID: 44557 "Drupal < 7.58 - 'Drupalgeddon3' (Authenticated) Remote Code (Metasploit)"
[M]  EDB-ID: 35415 "Drupal < 7.34 - Denial of Service"
[M]  EDB-ID: 34984 "Drupal 7.0 < 7.31 - 'Drupalgeddon' SQL Injection (PoC) (Reset Password) (1)"
[M]  EDB-ID: 34992 "Drupal 7.0 < 7.31 - 'Drupalgeddon' SQL Injection (Add Admin User)"
[M]  EDB-ID: 34993 "Drupal 7.0 < 7.31 - 'Drupalgeddon' SQL Injection (PoC) (Reset Password) (2)"
[M]  EDB-ID: 35150 "Drupal 7.0 < 7.31 - 'Drupalgeddon' SQL Injection (Remote Code Execution)"
[M]  EDB-ID: 44355 "Drupal 7.0 < 7.31 - 'Drupalgeddon' SQL Injection (Admin Session)"
[I] Drupal Theme: bartik
[-] Enumerating Drupal Usernames via "Views" Module...
[-] Enumerating Drupal Usernames via "/user/"...
[I] Autocomplete Off Not Found: http://10.0.0.1/user/
[-] Drupal Default Files: 
[-] Drupal is likely to have a large number of default files
[-] Would you like to list them all?
```
