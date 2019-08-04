---
tags: [snmp,network]
---
# snmpbw.pl

## References

SNMP data gather scripts.

- https://github.com/dheiland-r7/snmp

## Dependencies

For ArchLinux:

```
# pacman -S perl-netaddr-ip --asdeps 
```

## Example of execution

```
$ sudo perl ~/CTF/tools/snmpbw/snmpbw.pl 10.0.0.1 public 2 1
SNMP query:       10.0.0.1
Queue count:      0
SNMP SUCCESS:     10.0.0.1

$ ls -lh 10.0.0.1.snmp
-rw-r--r-- 1 noraj noraj 2,2K mai   31 18:27 10.0.0.1.snmp
```
