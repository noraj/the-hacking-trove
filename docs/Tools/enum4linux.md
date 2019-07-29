---
tags: [smb,samba]
---
# enum4linux

## References

Windows Samba enumeration tool.

`enum4linux` is a perl wrapper around `smbclient`, `rpcclient`, net and `nmblookup`.

- https://github.com/portcullislabs/enum4linux
- https://inventory.rawsec.ml/tools.html#enum4linux

## Example of execution

Enum all with `-a` option.

```
$ enum4linux -a 10.0.0.1
...
================================================== 
|    Enumerating Workgroup/Domain on 10.0.0.1    |
================================================== 
[+] Got domain/workgroup name: MYGROUP

========================================== 
|    Nbtstat Information for 10.0.0.1    |
========================================== 
Looking up status of 10.0.0.1
        HOSTNAME           <00> -         B <ACTIVE>  Workstation Service
        HOSTNAME           <03> -         B <ACTIVE>  Messenger Service
        HOSTNAME           <20> -         B <ACTIVE>  File Server Service
        ..__MSBROWSE__. <01> - <GROUP> B <ACTIVE>  Master Browser
        MYGROUP         <00> - <GROUP> B <ACTIVE>  Domain/Workgroup Name
        MYGROUP         <1d> -         B <ACTIVE>  Master Browser
        MYGROUP         <1e> - <GROUP> B <ACTIVE>  Browser Service Elections

        MAC Address = 00-00-00-00-00-00

=================================== 
|    Session Check on 10.0.0.1    |
=================================== 
[+] Server 10.0.0.1 allows sessions using username '', password ''

========================================= 
|    Getting domain SID for 10.0.0.1    |
========================================= 
Unable to initialize messaging context
Domain Name: MYGROUP
Domain Sid: (NULL SID)
[+] Can't determine if host is part of domain or part of a workgroup

==================================== 
|    OS information on 10.0.0.1    |
==================================== 
Use of uninitialized value $os_info in concatenation (.) or string at /usr/bin/enum4linux line 464.
[+] Got OS info for 10.0.0.1 from smbclient: 
[+] Got OS info for 10.0.0.1 from srvinfo:
Unable to initialize messaging context
        HOSTNAME          Wk Sv PrQ Unx NT SNT Samba Server
        platform_id     :       500
        os version      :       4.5
        server type     :       0x9a03

...

======================================= 
|    Share Enumeration on 10.0.0.1    |
======================================= 
Unable to initialize messaging context

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       IPC Service (Samba Server)
        ADMIN$          IPC       IPC Service (Samba Server)
Reconnecting with SMB1 for workgroup listing.

        Server               Comment
        ---------            -------
        HOSTNAME                Samba Server
        HOST2               Samba Server

        Workgroup            Master
        ---------            -------
        ACME                 HOST7
        MSHOME               HOST3
        MYGROUP              HOSTNAME
        DOMAIN                HOST4
        DOMAIN.LOCAL          HOST5
        WORKGROUP            HOST6

[+] Attempting to map shares on 10.0.0.1
//10.0.0.1/IPC$       [E] Can't understand response:
Unable to initialize messaging context
NT_STATUS_NETWORK_ACCESS_DENIED listing \*
//10.0.0.1/ADMIN$     [E] Can't understand response:
Unable to initialize messaging context
tree connect failed: NT_STATUS_WRONG_PASSWORD

============================ 
|    Groups on 10.0.0.1    |
============================ 

[+] Getting builtin groups:
group:[Administrators] rid:[0x220]
group:[Users] rid:[0x221]
group:[Guests] rid:[0x222]
group:[Power Users] rid:[0x223]
group:[Account Operators] rid:[0x224]
group:[System Operators] rid:[0x225]
group:[Print Operators] rid:[0x226]
group:[Backup Operators] rid:[0x227]
group:[Replicator] rid:[0x228]

[+] Getting builtin group memberships:
Group 'Guests' (RID: 546) has member: Couldn't find group Guests
Group 'Replicator' (RID: 552) has member: Couldn't find group Replicator
Group 'Backup Operators' (RID: 551) has member: Couldn't find group Backup Operators
Group 'Power Users' (RID: 547) has member: Couldn't find group Power Users
Group 'System Operators' (RID: 549) has member: Couldn't find group System Operators
Group 'Administrators' (RID: 544) has member: Couldn't find group Administrators
Group 'Print Operators' (RID: 550) has member: Couldn't find group Print Operators
Group 'Account Operators' (RID: 548) has member: Couldn't find group Account Operators
Group 'Users' (RID: 545) has member: Couldn't find group Users

[+] Getting local groups:
group:[sys] rid:[0x3ef]
group:[tty] rid:[0x3f3]
group:[disk] rid:[0x3f5]
group:[mem] rid:[0x3f9]
group:[kmem] rid:[0x3fb]
group:[wheel] rid:[0x3fd]
group:[man] rid:[0x407]
group:[dip] rid:[0x439]
group:[lock] rid:[0x455]
group:[users] rid:[0x4b1]
group:[slocate] rid:[0x413]
group:[floppy] rid:[0x40f]
group:[utmp] rid:[0x415]

[+] Getting local group memberships:
Group 'slocate' (RID: 1043) has member: Couldn't list alias members
Group 'floppy' (RID: 1039) has member: Couldn't list alias members
Group 'kmem' (RID: 1019) has member: Couldn't list alias members
Group 'disk' (RID: 1013) has member: Couldn't list alias members
Group 'dip' (RID: 1081) has member: Couldn't list alias members
Group 'man' (RID: 1031) has member: Couldn't list alias members
Group 'utmp' (RID: 1045) has member: Couldn't list alias members
Group 'lock' (RID: 1109) has member: Couldn't list alias members
Group 'sys' (RID: 1007) has member: Couldn't list alias members
Group 'wheel' (RID: 1021) has member: Couldn't list alias members
Group 'mem' (RID: 1017) has member: Couldn't list alias members
Group 'tty' (RID: 1011) has member: Couldn't list alias members
Group 'users' (RID: 1201) has member: Couldn't list alias members

[+] Getting domain groups:
group:[Domain Admins] rid:[0x200]
group:[Domain Users] rid:[0x201]

[+] Getting domain group memberships:
Group 'Domain Users' (RID: 513) has member: Couldn't find group Domain Users
Group 'Domain Admins' (RID: 512) has member: Couldn't find group Domain Admins

 ===================================================================== 
|    Users on 10.0.0.1 via RID cycling (RIDS: 500-550,1000-1050)    |
 ===================================================================== 
[I] Found new SID: S-1-5-21-2974263341-3895402545-469881541
[+] Enumerating users using SID S-1-5-21-2974263341-3895402545-469881541 and logon username '', password ''
S-1-5-21-2974263341-3895402545-469881541-500 HOSTNAME\Administrator (Local User)
S-1-5-21-2974263341-3895402545-469881541-501 HOSTNAME\(ý ┐ (Local User)
S-1-5-21-2974263341-3895402545-469881541-502 HOSTNAME\unix_group.2147483399 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-503 HOSTNAME\unix_group.2147483399 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-504 HOSTNAME\unix_group.2147483400 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-505 HOSTNAME\unix_group.2147483400 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-506 HOSTNAME\unix_group.2147483401 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-507 HOSTNAME\unix_group.2147483401 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-508 HOSTNAME\unix_group.2147483402 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-509 HOSTNAME\unix_group.2147483402 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-510 HOSTNAME\unix_group.2147483403 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-511 HOSTNAME\unix_group.2147483403 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-512 HOSTNAME\unix_group.2147483404 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-513 HOSTNAME\unix_group.2147483404 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-514 HOSTNAME\unix_group.2147483405 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-515 HOSTNAME\unix_group.2147483405 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-516 HOSTNAME\unix_group.2147483406 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-517 HOSTNAME\unix_group.2147483406 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-518 HOSTNAME\unix_group.2147483407 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-519 HOSTNAME\unix_group.2147483407 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-520 HOSTNAME\unix_group.2147483408 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-521 HOSTNAME\unix_group.2147483408 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-522 HOSTNAME\unix_group.2147483409 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-523 HOSTNAME\unix_group.2147483409 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-524 HOSTNAME\unix_group.2147483410 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-525 HOSTNAME\unix_group.2147483410 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-526 HOSTNAME\unix_group.2147483411 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-527 HOSTNAME\unix_group.2147483411 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-528 HOSTNAME\unix_group.2147483412 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-529 HOSTNAME\unix_group.2147483412 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-530 HOSTNAME\unix_group.2147483413 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-531 HOSTNAME\unix_group.2147483413 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-532 HOSTNAME\unix_group.2147483414 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-533 HOSTNAME\unix_group.2147483414 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-534 HOSTNAME\unix_group.2147483415 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-535 HOSTNAME\unix_group.2147483415 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-536 HOSTNAME\unix_group.2147483416 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-537 HOSTNAME\unix_group.2147483416 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-538 HOSTNAME\unix_group.2147483417 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-539 HOSTNAME\unix_group.2147483417 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-540 HOSTNAME\unix_group.2147483418 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-541 HOSTNAME\unix_group.2147483418 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-542 HOSTNAME\unix_group.2147483419 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-543 HOSTNAME\unix_group.2147483419 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-544 HOSTNAME\unix_group.2147483420 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-545 HOSTNAME\unix_group.2147483420 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-546 HOSTNAME\unix_group.2147483421 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-547 HOSTNAME\unix_group.2147483421 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-548 HOSTNAME\unix_group.2147483422 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-549 HOSTNAME\unix_group.2147483422 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-550 HOSTNAME\unix_group.2147483423 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1000 HOSTNAME\root (Local User)
S-1-5-21-2974263341-3895402545-469881541-1001 HOSTNAME\root (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1002 HOSTNAME\bin (Local User)
S-1-5-21-2974263341-3895402545-469881541-1003 HOSTNAME\bin (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1004 HOSTNAME\daemon (Local User)
S-1-5-21-2974263341-3895402545-469881541-1005 HOSTNAME\daemon (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1006 HOSTNAME\adm (Local User)
S-1-5-21-2974263341-3895402545-469881541-1007 HOSTNAME\sys (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1008 HOSTNAME\lp (Local User)
S-1-5-21-2974263341-3895402545-469881541-1009 HOSTNAME\adm (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1010 HOSTNAME\sync (Local User)
S-1-5-21-2974263341-3895402545-469881541-1011 HOSTNAME\tty (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1012 HOSTNAME\shutdown (Local User)
S-1-5-21-2974263341-3895402545-469881541-1013 HOSTNAME\disk (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1014 HOSTNAME\halt (Local User)
S-1-5-21-2974263341-3895402545-469881541-1015 HOSTNAME\lp (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1016 HOSTNAME\mail (Local User)
S-1-5-21-2974263341-3895402545-469881541-1017 HOSTNAME\mem (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1018 HOSTNAME\news (Local User)
S-1-5-21-2974263341-3895402545-469881541-1019 HOSTNAME\kmem (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1020 HOSTNAME\uucp (Local User)
S-1-5-21-2974263341-3895402545-469881541-1021 HOSTNAME\wheel (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1022 HOSTNAME\operator (Local User)
S-1-5-21-2974263341-3895402545-469881541-1023 HOSTNAME\unix_group.11 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1024 HOSTNAME\games (Local User)
S-1-5-21-2974263341-3895402545-469881541-1025 HOSTNAME\mail (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1026 HOSTNAME\gopher (Local User)
S-1-5-21-2974263341-3895402545-469881541-1027 HOSTNAME\news (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1028 HOSTNAME\ftp (Local User)
S-1-5-21-2974263341-3895402545-469881541-1029 HOSTNAME\uucp (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1030 HOSTNAME\unix_user.15 (Local User)
S-1-5-21-2974263341-3895402545-469881541-1031 HOSTNAME\man (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1032 HOSTNAME\unix_user.16 (Local User)
S-1-5-21-2974263341-3895402545-469881541-1033 HOSTNAME\unix_group.16 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1034 HOSTNAME\unix_user.17 (Local User)
S-1-5-21-2974263341-3895402545-469881541-1035 HOSTNAME\unix_group.17 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1036 HOSTNAME\unix_user.18 (Local User)
S-1-5-21-2974263341-3895402545-469881541-1037 HOSTNAME\unix_group.18 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1038 HOSTNAME\unix_user.19 (Local User)
S-1-5-21-2974263341-3895402545-469881541-1039 HOSTNAME\floppy (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1040 HOSTNAME\unix_user.20 (Local User)
S-1-5-21-2974263341-3895402545-469881541-1041 HOSTNAME\games (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1042 HOSTNAME\unix_user.21 (Local User)
S-1-5-21-2974263341-3895402545-469881541-1043 HOSTNAME\slocate (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1044 HOSTNAME\unix_user.22 (Local User)
S-1-5-21-2974263341-3895402545-469881541-1045 HOSTNAME\utmp (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1046 HOSTNAME\squid (Local User)
S-1-5-21-2974263341-3895402545-469881541-1047 HOSTNAME\squid (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1048 HOSTNAME\unix_user.24 (Local User)
S-1-5-21-2974263341-3895402545-469881541-1049 HOSTNAME\unix_group.24 (Local Group)
S-1-5-21-2974263341-3895402545-469881541-1050 HOSTNAME\unix_user.25 (Local User)
...
```
