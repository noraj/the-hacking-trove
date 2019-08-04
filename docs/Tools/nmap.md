---
tags: [network,scanner]
---
# Nmap

## References

- Nmap: Tool for network discovery and security auditing: https://nmap.org/
- NMapGUI: Advanced GUI for Nmap https://github.com/danicuestasuarez/NMapGUI
- Zenmap: Nmap GUI https://nmap.org/zenmap/
- https://inventory.rawsec.ml/tools.html#Nmap
- https://inventory.rawsec.ml/tools.html#NMapGUI
- https://inventory.rawsec.ml/tools.html#Zenmap

## Examples of commands

Host discovery scan (basic with ping):

```
nmap -sn 10.0.0.0/24
nmap -sP 10.0.0.0/24
```

Scan all ports, TCP SYN, default script, service/version info with fast timing and output in all format:

```
sudo nmap -p- -sSCV -T4 10.0.0.1 -oA 10.0.0.1
```

1000 most common ports with TCP CONNECT method:

```
$ nmap -sT 192.168.0.1
```

OS Fingerprinting:

```
# sudo nmap -O 192.168.0.1
```

Aggressive scan (This enables OS detection (-O), version scanning (-sV), script scanning (-sC) and traceroute (--traceroute)):

```
$ nmap -A 192.168.0.1
```

Deep scan (all ports, `-v` to show open port directly when found)

```
$ nmap -v -p- -sT 192.168.0.1
```

Top 1000 ports for an UDP scan:

```
$ sudo nmap -sU --top-ports 1000 -T4 10.0.0.1 -oA 10.0.0.1_UDP -v
```
