---
tags:
  - mssql
  - windows
---
# sqsh

## References

The problem can be to find a SQL client compatible with **old** versions of MS SQL on **Linux**.
Lot of SQL clients that are compatible with MS SQL are in fact compatible with MS SQL Server 2005+ but not 2003/2000.
Here `sqsh` comes to the rescue.

- Official source: https://sourceforge.net/projects/sqsh/
- [AUR package](https://aur.archlinux.org/packages/sqsh/)

## Example of execution

Connect to shell (one time)

```
$ sqsh -U sa -P password -S 10.0.0.1:1433 -D mydb
sqsh-2.5.16.1 Copyright (C) 1995-2001 Scott C. Gray
Portions Copyright (C) 2004-2014 Michael Peppler and Martin Wesdorp
This is free software with ABSOLUTELY NO WARRANTY
For more information type '\warranty'
[1] 10.0.0.1:1433.mydb.1>
```

Pretty output `go -m pretty`.

Alternatively it is possible to not use any option and configure `freetds.conf` and `~/.sqshrc` but is far less handy/versatile: https://www.adampalmer.me/iodigitalsec/2013/08/10/accessing-and-hacking-mssql-from-backtrack-linux/
