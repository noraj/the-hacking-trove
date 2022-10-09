---
tags: [cracking,password,hash]
---
# John The Ripper

=== Info
- **Description**: Hash cracking tool.
- Version tested: v1.9.0-Jumbo-1
- Review date: 09/10/2022
- [Website John The Ripper](http://www.openwall.com/john/)
- [Website John The Ripper, Jumbo version](http://www.openwall.com/john/) (community-enhanced version of John The Ripper)
- [Rawsec Inventory John The Ripper](https://inventory.raw.pm/tools.html#John%20The%20Ripper)
- [Rawsec Inventory John The Ripper, Jumbo version](https://inventory.raw.pm/tools.html#John%20the%20Ripper,%20Jumbo%20version)
===

## Unshadow

Unshadow (combine passwd and shadow files) linux passwords:

```
$ unshadow passwd1 shadow1 > unshadow.txt
```

## Cracking

Crack all hashes:

```
$ john unshadow.txt
```

Crack only one account:

```
$ john --users=toto unshadow.txt
$ john --users=1055 unshadow.txt
```

Print cracked passwords:

```
$ john --show unshadow.txt
```

## Custom mutations rules

Generate a dict based on a rule and then use it to crack

```
$ john --wordlist=/usr/share/wordlists/password/rockyou.txt --stdout --rules:norajCommon02 > dict.txt
$ john hash.txt --format=raw-md5 --wordlist=./dict.txt
```

Use a mutation rule directly

```
$ john hash.txt --format=raw-md5 --wordlist=/usr/share/wordlists/password/rockyou.txt --rules=norajCommon02
```

References:

- [Custom Credential Mutations](https://metasploit.help.rapid7.com/docs/custom-credential-mutations)
- [Wordlist rules syntax](https://www.openwall.com/john/doc/RULES.shtml)

## Benchmark

```
$ john --test
```

## Maximum password length

- https://www.notsosecure.com/maximum-password-length-reached/

## Dynamic types

We can find a list of advanced hash types in [dynamic.conf](https://github.com/openwall/john/blob/bleeding-jumbo/run/dynamic.conf) or [dynamic_preloads.c](https://github.com/openwall/john/blob/bleeding-jumbo/src/dynamic_preloads.c).
There is a large list of ready to use types defined in there.

For example you can find this line for md5 chained 4 times:

```
# dynamic_1001: md5(md5(md5(md5($p))))
```

Let's generate such a hash for the test with [ctf-party](https://noraj.github.io/ctf-party/).

```shell
ctf-party 'noraj' md5 md5 md5 md5 > /tmp/hash.txt
```

Attempting to crack it works just fine:

```
$ john /tmp/hash.txt -w=/usr/share/wordlists/passwords/rockyou.txt --format=dynamic_1001
Using default input encoding: UTF-8
Loaded 1 password hash (dynamic_1001 [md5(md5(md5(md5($p)))) 128/128 AVX 4x3])
Warning: no OpenMP support for this hash type, consider --fork=4
Press 'q' or Ctrl-C to abort, almost any other key for status
noraj            (?)
1g 0:00:00:01 DONE (2022-10-09 15:38) 0.8620g/s 4324Kp/s 4324Kc/s 4324KC/s norge22..norah2004
Use the "--show --format=dynamic_1001" options to display all of the cracked passwords reliably
Session completed
```

However if we want to crack a very custom format that is not in the list, we can forge some that are not in the list.

```shell
ctf-party 'noraj' md5 sha1 sha2_256 sha2_384 sha2_512 > /tmp/hash.txt
```

```
$ john /tmp/hash.txt -w=/usr/share/wordlists/passwords/rockyou.txt --format='dynamic=sha512(sha384(sha256(sha1(md5($p)))))'
Using default input encoding: UTF-8
Loaded 1 password hash (dynamic=sha512(sha384(sha256(sha1(md5($p))))) [128/128 AVX 2x])
Warning: no OpenMP support for this hash type, consider --fork=4
Press 'q' or Ctrl-C to abort, almost any other key for status
noraj            (?)
1g 0:00:00:04 DONE (2022-10-09 15:47) 0.2197g/s 1102Kp/s 1102Kc/s 1102KC/s norakopa5212..nop0890069746
Use the "--show --format=dynamic=sha512(sha384(sha256(sha1(md5($p)))))" options to display all of the cracked passwords reliably
Session completed
```
