---
tags: [smb,samba,ldap,rpc]
---
# enum4linux-ng

=== Info
- **Description**: A next generation version of enum4linux (a Windows/Samba enumeration tool) with additional features like JSON/YAML export.
- Version tested: v1.1.0
- Review date: 09/10/2022
- [Source](https://github.com/cddmp/enum4linux-ng)
- [Rawsec Inventory](https://inventory.raw.pm/tools.html#enum4linux-ng)
===

## Example of execution

Running `enum4linux-ng` without any enumeration option is equivalent to running it with `-A` (un mostly all common modules), which is similar to enum4linux `-a` option.

[!ref enum4linux](/tools/enum4linux.md)

It's possible to save all the results as a JSON file so you can use them with other tools.

```
$ enum4linux-ng -A 10.0.0.1 -u 'svc_user' -p 'azerty1234' -oJ enum4linux-ng_output
```

Then a quick Ruby script would allow you to extract all users or all groups from the AD in a parsable way:

```ruby
require 'json'

data = JSON.load_file('enum4linux-ng_output.json')

case ARGV[0]
when 'users'
  puts data['users'].map { |_k,v| v['username'] }
when 'users_id'
  puts data['users'].map {|k,v| "#{k},#{v['username']}" }
when 'groups'
  puts data['groups'].map { |_k,v| v['groupname'] }
when 'groups_id'
  puts data['groups'].map {|k,v| "#{k},#{v['groupname']}" }
else
  puts '[+] Usage: <users|users_id|groups|groups_id>'
end
```
