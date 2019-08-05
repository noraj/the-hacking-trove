---
tags: [network,analyzer]
---
# Tcpdump

## References

tcpdump is a powerful network packet analyzer.

- Official site: https://www.tcpdump.org/

## Read a pcap:

```
$ tcpdump -r file.pcap
```

## packet filter syntax

Filter destination/source IPs and ports:

```
$ tcpdump -n src host 172.16.40.10 -r file.pcap
$ tcpdump -n dst host 172.16.40.10 -r file.pcap
$ tcpdump -n port 81 -r file.pcap
```

packet filter syntax: [Pcap-filter](https://www.manpagez.com/man/7/pcap-filter/) man page

## TCP flags

Tcpflags are some combination of S (SYN), F (FIN), P (PUSH), R (RST), U (URG), W (ECN CWR), E (ECN-Echo) or '.' (ACK), or 'none' if no flags are set.

For example `tcp[13]` may be replaced with `tcp[tcpflags]`. The following TCP flag field values are also available: `tcp-fin`, `tcp-syn`, `tcp-rst`, `tcp-push`, `tcp-ack`, `tcp-urg`.

Example: To print the start and end packets (the SYN and FIN packets) of each TCP conversation that involves a non-local host.

```
$ tcpdump 'tcp[tcpflags] & (tcp-syn|tcp-fin) != 0 and not src and dst net localnet
$ tcpdump 'tcp[13] = 3 and not src and dst net localnet'
```

Another example with ACK or PSH:

```
$ tcpdump 'tcp[tcpflags] & (tcp-ack|tcp-push) != 0 and not src and dst net localnet
$ tcpdump 'tcp[13] = 24 and not src and dst net localnet'
```

Note: `==` can be use instead of `=` for strict (AND) instead of (OR) when there are several flags.

Flags order:

```
|C|E|U|A|P|R|S|F|
|---------------|
|0 0 0 0 0 0 0 0|
|---------------|
|7 6 5 4 3 2 1 0|
```

## TCP header

```
0                            15                              31
-----------------------------------------------------------------
|          source port          |       destination port        |
-----------------------------------------------------------------
|                        sequence number                        |
-----------------------------------------------------------------
|                     acknowledgment number                     |
-----------------------------------------------------------------
|  HL   | rsvd  |C|E|U|A|P|R|S|F|        window size            |
-----------------------------------------------------------------
|         TCP checksum          |       urgent pointer          |
-----------------------------------------------------------------
```

## Options

- `-n`: Don't convert addresses (i.e., host addresses, port numbers, etc.) to names.
- print the data of each packet
    - `-x`: (minus its link level header) in hex.
    - `-xx`: including its link level header, in hex.
    - `-X`: (minus its link level header) in hex and ASCII.
    - `-XX`: including its link level header, in hex and ASCII.
    - `-A`: (minus its link level header) in ASCII.
