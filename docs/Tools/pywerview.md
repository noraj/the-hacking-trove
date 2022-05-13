---
tags: [python,ad,ldap]
---
# pywerview

=== Info
- **Description**: A (partial) Python rewriting of PowerSploit's PowerView
- Version tested: v0.4.0
- Review date: 13/05/2022
- [Source](https://github.com/the-useless-one/pywerview)
- [Rawsec Inventory](https://inventory.rawsec.ml/tools.html#pywerview)
===

## Example of execution

Having a AD domain account (user A), query info about user B account via LDAP:

```
$ pywerview get-netuser -w <domain.local> -u <userA> -p <passwordA> -t <domain_controller> --username <query_userB>
```

Example [THM room Attacktive Directory](https://tryhackme.com/room/attacktivedirectory):

```
$ pywerview get-netuser -w spookysec.local -u svc-admin -p management2005 -t 10.10.156.68 --username backup
objectclass:           top, person, organizationalPerson, user
cn:                    backup
givenname:             backup
distinguishedname:     CN=backup,OU=Administrator,DC=spookysec,DC=local
instancetype:          4
whencreated:           2020-04-04 19:57:04+00:00
whenchanged:           2020-04-04 19:58:14+00:00
displayname:           backup
usncreated:            16426
usnchanged:            16434
name:                  backup
objectguid:            {92e326a7-1a92-43f9-aa2b-9aa51ba955e6}
useraccountcontrol:    NORMAL_ACCOUNT, DONT_EXPIRE_PASSWORD
badpwdcount:           0
codepage:              0
countrycode:           0
badpasswordtime:       2020-04-04 20:06:43.519606+00:00
lastlogoff:            1601-01-01 00:00:00+00:00
lastlogon:             2020-04-04 20:07:32.221279+00:00
pwdlastset:            2020-04-04 19:57:05.720037+00:00
primarygroupid:        513
objectsid:             S-1-5-21-3591857110-2884097990-301047963-1118
accountexpires:        9999-12-31 23:59:59.999999+00:00
logoncount:            1
samaccountname:        backup
samaccounttype:        805306368
userprincipalname:     backup@spookysec.local
objectcategory:        CN=Person,CN=Schema,CN=Configuration,DC=spookysec,DC=local
dscorepropagationdata: 2020-04-04 20:04:15+00:00, 2020-04-04 20:01:23+00:00, 2020-04-04 19:58:09+00:00,
                       1601-01-01 18:16:33+00:00
lastlogontimestamp:    2020-04-04 19:58:14.983641+00:00

$ pywerview get-netuser -w spookysec.local -u svc-admin -p management2005 -t 10.10.156.68 --username svc-admin
objectclass:                   top, person, organizationalPerson, user
cn:                            svc admin
sn:                            admin
givenname:                     svc
distinguishedname:             CN=svc admin,OU=Staff,DC=spookysec,DC=local
instancetype:                  4
whencreated:                   2020-04-04 18:57:55+00:00
whenchanged:                   2022-05-13 17:30:31+00:00
displayname:                   svc admin
usncreated:                    12928
memberof:                      CN=CompStaff,DC=spookysec,DC=local, CN=Remote Desktop Users,CN=Builtin,DC=spookysec,DC=local
usnchanged:                    57374
name:                          svc admin
objectguid:                    {d2fe7d1f-cb38-43db-a905-984b1bc99c23}
useraccountcontrol:            NORMAL_ACCOUNT, DONT_EXPIRE_PASSWORD, DONT_REQ_PREAUTH
badpwdcount:                   0
codepage:                      0
countrycode:                   0
badpasswordtime:               1601-01-01 00:00:00+00:00
lastlogoff:                    1601-01-01 00:00:00+00:00
lastlogon:                     2020-04-04 19:27:49.468676+00:00
pwdlastset:                    2020-04-04 18:57:56.747414+00:00
primarygroupid:                513
objectsid:                     S-1-5-21-3591857110-2884097990-301047963-1114
accountexpires:                9999-12-31 23:59:59.999999+00:00
logoncount:                    3
samaccountname:                svc-admin
samaccounttype:                805306368
userprincipalname:             svc-admin@spookysec.local
objectcategory:                CN=Person,CN=Schema,CN=Configuration,DC=spookysec,DC=local
dscorepropagationdata:         2020-04-04 20:04:15+00:00, 2020-04-04 20:01:23+00:00, 2020-04-04 19:58:09+00:00,
                               2020-04-04 19:45:45+00:00, 1601-07-14 22:36:49+00:00
lastlogontimestamp:            2022-05-13 17:30:31.816168+00:00
msds-supportedencryptiontypes: 0
```

List groups:

```
$ pywerview get-netgroup -w spookysec.local -u svc-admin -p management2005 -t 10.10.156.68 --username svc-admin
samaccountname: CompStaff
samaccountname: Remote Desktop Users
```

Get info about the domain controller:

```
$ pywerview get-netdomaincontroller -w spookysec.local -u svc-admin -p management2005 -t 10.10.156.68
objectclass:                   top, person, organizationalPerson, user, computer
cn:                            ATTACKTIVEDIREC
distinguishedname:             CN=ATTACKTIVEDIREC,OU=Domain Controllers,DC=spookysec,DC=local
instancetype:                  4
whencreated:                   2020-04-04 18:40:08+00:00
whenchanged:                   2022-05-13 17:23:40+00:00
usncreated:                    12293
usnchanged:                    57363
name:                          ATTACKTIVEDIREC
objectguid:                    {57ee0846-b255-42bb-84d3-ba32b266e1e5}
useraccountcontrol:            SERVER_TRUST_ACCOUNT, TRUSTED_FOR_DELEGATION
badpwdcount:                   0
codepage:                      0
countrycode:                   0
badpasswordtime:               1601-01-01 00:00:00+00:00
lastlogoff:                    1601-01-01 00:00:00+00:00
lastlogon:                     2022-05-13 17:25:20.223974+00:00
localpolicyflags:              0
pwdlastset:                    2022-05-13 17:23:14.989624+00:00
primarygroupid:                516
objectsid:                     S-1-5-21-3591857110-2884097990-301047963-1000
accountexpires:                9999-12-31 23:59:59.999999+00:00
logoncount:                    44
samaccountname:                ATTACKTIVEDIREC$
samaccounttype:                805306369
operatingsystem:               Windows Server 2019 Standard
operatingsystemversion:        10.0 (17763)
serverreferencebl:
                               CN=ATTACKTIVEDIREC,CN=Servers,CN=Default-First-Site-Name,CN=Sites,CN=Configuration,DC=spookysec,DC=local
dnshostname:                   AttacktiveDirectory.spookysec.local
ridsetreferences:              CN=RID Set,CN=ATTACKTIVEDIREC,OU=Domain Controllers,DC=spookysec,DC=local
serviceprincipalname:          Dfsr-12F9A27C-BF97-4787-9364-D31B6C55EB04/AttacktiveDirectory.spookysec.local,
                               ldap/AttacktiveDirectory.spookysec.local/ForestDnsZones.spookysec.local,
                               ldap/AttacktiveDirectory.spookysec.local/DomainDnsZones.spookysec.local, TERMSRV/ATTACKTIVEDIREC,
                               TERMSRV/AttacktiveDirectory.spookysec.local, DNS/AttacktiveDirectory.spookysec.local,
                               GC/AttacktiveDirectory.spookysec.local/spookysec.local,
                               RestrictedKrbHost/AttacktiveDirectory.spookysec.local, RestrictedKrbHost/ATTACKTIVEDIREC,
                               RPC/22efa0ac-0a79-44f5-a04f-4caf1260c1ad._msdcs.spookysec.local, HOST/ATTACKTIVEDIREC/THM-AD,
                               HOST/AttacktiveDirectory.spookysec.local/THM-AD, HOST/ATTACKTIVEDIREC,
                               HOST/AttacktiveDirectory.spookysec.local, HOST/AttacktiveDirectory.spookysec.local/spookysec.local,
                               E3514235-4B06-11D1-AB04-00C04FC2DCD2/22efa0ac-0a79-44f5-a04f-4caf1260c1ad/spookysec.local,
                               ldap/ATTACKTIVEDIREC/THM-AD, ldap/22efa0ac-0a79-44f5-a04f-4caf1260c1ad._msdcs.spookysec.local,
                               ldap/AttacktiveDirectory.spookysec.local/THM-AD, ldap/ATTACKTIVEDIREC,
                               ldap/AttacktiveDirectory.spookysec.local, ldap/AttacktiveDirectory.spookysec.local/spookysec.local
objectcategory:                CN=Computer,CN=Schema,CN=Configuration,DC=spookysec,DC=local
iscriticalsystemobject:        True
dscorepropagationdata:         2020-04-04 20:04:15+00:00, 2020-04-04 20:01:23+00:00, 2020-04-04 19:58:09+00:00,
                               2020-04-04 19:45:45+00:00, 1601-07-14 22:36:49+00:00
lastlogontimestamp:            2022-05-13 17:23:40.083342+00:00
msds-supportedencryptiontypes: 28
msds-generationid:             205838ad8e2abccf...
msdfsr-computerreferencebl:
                               CN=ATTACKTIVEDIREC,CN=Topology,CN=Domain System Volume,CN=DFSR-GlobalSettings,CN=System,DC=spookysec,DC=local
```

Get a list of all current OUs in the domain:

```
$ pywerview get-netou -w spookysec.local -u svc-admin -p management2005 -t 10.10.156.68
distinguishedname: OU=Administrator,DC=spookysec,DC=local
distinguishedname: OU=Staff,DC=spookysec,DC=local
distinguishedname: OU=Domain Controllers,DC=spookysec,DC=local
```

Get a list of all current GPOs in the domain:

```
$ pywerview get-netgpo -w spookysec.local -u svc-admin -p management2005 -t 10.10.156.68
objectclass:              top, container, groupPolicyContainer
cn:                       {6AC1786C-016F-11D2-945F-00C04fB984F9}
distinguishedname:        CN={6AC1786C-016F-11D2-945F-00C04fB984F9},CN=Policies,CN=System,DC=spookysec,DC=local
instancetype:             4
whencreated:              2020-04-04 18:39:30+00:00
whenchanged:              2020-04-04 19:23:08+00:00
displayname:              Default Domain Controllers Policy
usncreated:               5675
usnchanged:               13035
showinadvancedviewonly:   True
name:                     {6AC1786C-016F-11D2-945F-00C04fB984F9}
objectguid:               {abb1757e-8427-43b1-94a2-2a4cceab4cbb}
flags:                    0
versionnumber:            2
systemflags:              -1946157056
objectcategory:           CN=Group-Policy-Container,CN=Schema,CN=Configuration,DC=spookysec,DC=local
iscriticalsystemobject:   True
gpcfunctionalityversion:  2
gpcfilesyspath:           \\spookysec.local\sysvol\spookysec.local\Policies\{6AC1786C-016F-11D2-945F-00C04fB984F9}
gpcmachineextensionnames: [{827D319E-6EAC-11D2-A4EA-00C04F79F83A}{803E14A0-B4FB-11D0-A0D0-00A0C90F574B}]
dscorepropagationdata:    2020-04-04 20:04:15+00:00, 2020-04-04 20:01:23+00:00, 2020-04-04 19:58:09+00:00,
                          2020-04-04 19:45:45+00:00, 1601-01-01 00:00:00+00:00

objectclass:              top, container, groupPolicyContainer
cn:                       {31B2F340-016D-11D2-945F-00C04FB984F9}
distinguishedname:        CN={31B2F340-016D-11D2-945F-00C04FB984F9},CN=Policies,CN=System,DC=spookysec,DC=local
instancetype:             4
whencreated:              2020-04-04 18:39:30+00:00
whenchanged:              2020-04-04 19:15:37+00:00
displayname:              Default Domain Policy
usncreated:               5672
usnchanged:               13012
showinadvancedviewonly:   True
name:                     {31B2F340-016D-11D2-945F-00C04FB984F9}
objectguid:               {93edd552-7e8d-4af2-82fe-708096d498bf}
flags:                    0
versionnumber:            61
systemflags:              -1946157056
objectcategory:           CN=Group-Policy-Container,CN=Schema,CN=Configuration,DC=spookysec,DC=local
iscriticalsystemobject:   True
gpcfunctionalityversion:  2
gpcfilesyspath:           \\spookysec.local\sysvol\spookysec.local\Policies\{31B2F340-016D-11D2-945F-00C04FB984F9}
gpcmachineextensionnames: [{35378EAC-683F-11D2-A89A-00C04FBBCFA2}{53D6AB1B-2488-11D1-A28C-00C04FB94F17}][{827D319E-6EAC-11D2-A4EA-00C04F79F83A}{803E14A0-B4FB-11D0-A0D0-00A0C90F574B}][{B1BE8D72-6EAC-11D2-A4EA-00C04F79F83A}{53D6AB1B-2488-11D1-A28C-00C04FB94F17}]
dscorepropagationdata:    2020-04-04 20:04:15+00:00, 2020-04-04 20:01:23+00:00, 2020-04-04 19:58:09+00:00,
                          2020-04-04 19:45:45+00:00, 1601-01-01 00:00:00+00:00
```

Returns the default domain or DC policy for the queried domain or DC:

```
$ pywerview get-domainpolicy -w spookysec.local -u svc-admin -p management2005 -t 10.10.156.68
unicode:         
        Unicode: yes
systemaccess:    
        MinimumPasswordLength:        0
        PasswordComplexity:           0
        PasswordHistorySize:          0
        LockoutBadCount:              0
        RequireLogonToChangePassword: 0
        ForceLogoffWhenHourExpire:    0
        ClearTextPassword:            0
        LSAAnonymousNameLookup:       1
kerberospolicy:  
        MaxTicketAge:         10
        MaxRenewAge:          7
        MaxServiceAge:        600
        MaxClockSkew:         5
        TicketValidateClient: 1
version:         
        signature: "$CHICAGO$"
        Revision:  1
registryvalues:  
        MACHINE\System\CurrentControlSet\Control\Lsa\EveryoneIncludesAnonymous:                   4, 1
        MACHINE\System\CurrentControlSet\Control\Lsa\RestrictAnonymousSAM:                        4, 0
        MACHINE\System\CurrentControlSet\Services\LanManServer\Parameters\RestrictNullSessAccess: 4, 0
        MACHINE\System\CurrentControlSet\Control\Lsa\NoLMHash:                                    4, 1
privilegerights: 
        SeInteractiveLogonRight:       Domain Users, Domain Admins, *S-1-5-32-544
        SeRemoteInteractiveLogonRight: Domain Users, Domain Admins, *S-1-5-32-544
```

Queries a host to return a list of available shares on the host:

```
$ pywerview get-netshare -w spookysec.local -u svc-admin -p management2005 --computername 10.10.156.68 
shi1_netname: ADMIN$
shi1_remark:  Remote Admin
shi1_type:    2147483648

shi1_netname: backup
shi1_remark:  
shi1_type:    0

shi1_netname: C$
shi1_remark:  Default share
shi1_type:    2147483648

shi1_netname: IPC$
shi1_remark:  Remote IPC
shi1_type:    2147483651

shi1_netname: NETLOGON
shi1_remark:  Logon server share 
shi1_type:    0

shi1_netname: SYSVOL
shi1_remark:  Logon server share 
shi1_type:    0
```
