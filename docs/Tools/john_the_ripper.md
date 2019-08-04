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

## Benchmark

```
$ john --test
```
