---
tags: [osint]
---
# Whois

Did you know you can query WHOIS databases not only online on some websites but also with the `whois` CLI tool? 

## Examples of execution

Whois works over TCP port 43.

Ask for domain information:

```
$ whois example.org

Domain Name: EXAMPLE.ORG
Registry Domain ID: D2328855-LROR
Registrar WHOIS Server:
Registrar URL:
Updated Date: 2015-08-19T20:25:53Z
Creation Date: 1995-08-31T04:00:00Z
Registry Expiry Date: 2010-08-30T04:00:00Z
Registrar Registration Expiration Date:
Registrar: ICANN
Registrar IANA ID: 376
Registrar Abuse Contact Email:
Registrar Abuse Contact Phone:
Reseller:
Domain Status: serverDeleteProhibited https://icann.org/epp#serverDeleteProhibited
Domain Status: serverRenewProhibited https://icann.org/epp#serverRenewProhibited
Domain Status: serverTransferProhibited https://icann.org/epp#serverTransferProhibited
Domain Status: serverUpdateProhibited https://icann.org/epp#serverUpdateProhibited
Registrant Organization: ICANN
Registrant State/Province: CA
Registrant Country: US
Name Server: A.IANA-SERVERS.NET
Name Server: B.IANA-SERVERS.NET
DNSSEC: signedDelegation
URL of the ICANN Whois Inaccuracy Complaint Form https://www.icann.org/wicf/)
>>> Last update of WHOIS database: 2019-08-05T22:05:24Z <<<

For more information on Whois status codes, please visit https://icann.org/epp

Access to Public Interest Registry WHOIS information is provided to assist persons in determining the contents of a domain name registration record in the Public Interest Registry registry database. The data in this record is provided by Public Interest Registry for informational purposes only, and Public Interest Registry does not guarantee its accuracy. This service is intended only for query-based access. You agree that you will use this data only for lawful purposes and that, under no circumstances will you use this data to (a) allow, enable, or otherwise support the transmission by e-mail, telephone, or facsimile of mass unsolicited, commercial advertising or solicitations to entities other than the data recipient's own existing customers; or (b) enable high volume, automated, electronic processes that send queries or data to the systems of Registry Operator, a Registrar, or Afilias except as reasonably necessary to register domain names or modify existing registrations. All rights reserved. Public Interest Registry reserves the right to modify these terms at any time. By submitting this query, you agree to abide by this policy.

The Registrar of Record identified in this output may have an RDDS service that can be queried for additional information on how to contact the Registrant, Admin, or Tech contact of the queried domain name.
```

Reverse lookup (by IP):

```
$ whois 35.185.44.232

#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at: https://www.arin.net/resources/registry/whois/tou/
#
# If you see inaccuracies in the results, please report at
# https://www.arin.net/resources/registry/whois/inaccuracy_reporting/
#
# Copyright 1997-2019, American Registry for Internet Numbers, Ltd.
#


NetRange:       35.184.0.0 - 35.191.255.255
CIDR:           35.184.0.0/13
NetName:        GOOGLE-CLOUD
NetHandle:      NET-35-184-0-0-1
Parent:         NET35 (NET-35-0-0-0-0)
NetType:        Direct Allocation
OriginAS:       
Organization:   Google LLC (GOOGL-2)
RegDate:        2016-10-11
Updated:        2016-10-17
Ref:            https://rdap.arin.net/registry/ip/35.184.0.0



OrgName:        Google LLC
OrgId:          GOOGL-2
Address:        1600 Amphitheatre Parkway
City:           Mountain View
StateProv:      CA
PostalCode:     94043
Country:        US
RegDate:        2006-09-29
Updated:        2017-12-21
Comment:        *** The IP addresses under this Org-ID are in use by Google Cloud customers *** 
Comment:        
Comment:        Direct all copyright and legal complaints to 
Comment:        https://support.google.com/legal/go/report
Comment:        
Comment:        Direct all spam and abuse complaints to 
Comment:        https://support.google.com/code/go/gce_abuse_report
Comment:        
Comment:        For fastest response, use the relevant forms above.
Comment:        
Comment:        Complaints can also be sent to the GC Abuse desk 
Comment:        (google-cloud-compliance@google.com) 
Comment:        but may have longer turnaround times.
Comment:        
Comment:        Complaints sent to any other POC will be ignored.
Ref:            https://rdap.arin.net/registry/entity/GOOGL-2


OrgAbuseHandle: GCABU-ARIN
OrgAbuseName:   GC Abuse
OrgAbusePhone:  +1-650-253-0000 
OrgAbuseEmail:  google-cloud-compliance@google.com
OrgAbuseRef:    https://rdap.arin.net/registry/entity/GCABU-ARIN

OrgNOCHandle: GCABU-ARIN
OrgNOCName:   GC Abuse
OrgNOCPhone:  +1-650-253-0000 
OrgNOCEmail:  google-cloud-compliance@google.com
OrgNOCRef:    https://rdap.arin.net/registry/entity/GCABU-ARIN

OrgTechHandle: ZG39-ARIN
OrgTechName:   Google LLC
OrgTechPhone:  +1-650-253-0000 
OrgTechEmail:  arin-contact@google.com
OrgTechRef:    https://rdap.arin.net/registry/entity/ZG39-ARIN


#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at: https://www.arin.net/resources/registry/whois/tou/
#
# If you see inaccuracies in the results, please report at
# https://www.arin.net/resources/registry/whois/inaccuracy_reporting/
#
# Copyright 1997-2019, American Registry for Internet Numbers, Ltd.
```
