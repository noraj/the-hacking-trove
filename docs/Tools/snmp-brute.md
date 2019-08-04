---
tags: [snmp,network]
---
# snmp-brute

## References

Fast SNMP brute force, enumeration, CISCO config downloader and password cracking script.

- https://github.com/SECFORCE/SNMP-Brute

## Example of execution

```
$ snmpbrute -t 10.0.0.1
   _____ _   ____  _______     ____             __     
  / ___// | / /  |/  / __ \   / __ )_______  __/ /____ 
  \__ \/  |/ / /|_/ / /_/ /  / __  / ___/ / / / __/ _ \
 ___/ / /|  / /  / / ____/  / /_/ / /  / /_/ / /_/  __/
/____/_/ |_/_/  /_/_/      /_____/_/   \__,_/\__/\___/ 

SNMP Bruteforce & Enumeration Script v1.0b
http://www.secforce.com / nikos.vassakis <at> secforce.com
###############################################################

Trying 199 community strings ...
10.0.0.1 : 161        Version (v1):   public
10.0.0.1 : 161        Version (v2c):  public
10.0.0.1 : 161        Version (v1):   public
10.0.0.1 : 161        Version (v2c):  public
Waiting for late packets (CTRL+C to stop)

Trying identified strings for READ-WRITE ...

Identified Community strings
        0) 10.0.0.1      public (v1)(RO)
        1) 10.0.0.1      public (v2c)(RO)
Select Community to Enumerate [0]:0

Enumerating with READ-WRITE Community string: public (v1)
################## Enumerating Routing Table (snmpwalk)
        Destination             Next Hop        Mask                    Metric  Interface       Type    Protocol        Age
        -----------             --------        ----                    ------  ---------       ----    --------        ---
        MIB                     MIB             MIB                      MIB       MIB          MIB       MIB           MIB


################## Enumerating ARP Table using: .1.3.6.1.2.1.3.1  (ARP address method B)
        IP              MAC                     V
        --              ---                     --


################## Enumerating ARP Table using: .1.3.6.1.2.1.3.1  (ARP address method A)
        IP              MAC                     V
        --              ---                     --


################## Enumerating SYSTEM Table using: iso.3.6.1.2.1.1  (SYSTEM Info)
...
```
