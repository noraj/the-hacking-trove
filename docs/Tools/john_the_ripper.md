---
tags: [cracking,password,hash]
---
# John The Ripper

## References

Password cracking tool

- John The Ripper: http://www.openwall.com/john/
- John The Ripper, Jumbo version: community-enhanced version of John The Ripper - http://www.openwall.com/john/
- https://inventory.rawsec.ml/tools.html#John%20The%20Ripper
- https://inventory.rawsec.ml/tools.html#John%20the%20Ripper,%20Jumbo%20version

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
