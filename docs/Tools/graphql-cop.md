---
tags: [graphql]
---
# GraphQL Cop

=== Info
- **Description**: Run common security tests against GraphQL API
- Version tested: v1.12
- Review date: 27/11/2022
- [Source](https://github.com/dolevf/graphql-cop)
- [Rawsec Inventory](https://inventory.raw.pm/tools.html#GraphQL%20Cop)
===
## Example of execution

```
$ graphql-cop -t http://noraj.test:5013/graphql
[HIGH] Alias Overloading - Alias Overloading with 100+ aliases is allowed (Denial of Service - /graphql)
[HIGH] Array-based Query Batching - Batch queries allowed with 10+ simultaneous queries (Denial of Service - /graphql)
[HIGH] Directive Overloading - Multiple duplicated directives allowed in a query (Denial of Service - /graphql)
[HIGH] Field Duplication - Queries are allowed with 500 of the same repeated field (Denial of Service - /graphql)
[LOW] Field Suggestions - Field Suggestions are Enabled (Information Leakage - /graphql)
[MEDIUM] GET Method Query Support - GraphQL queries allowed using the GET method (Possible Cross Site Request Forgery (CSRF) - /graphql)
[HIGH] Introspection - Introspection Query Enabled (Information Leakage - /graphql)
[HIGH] Introspection-based Circular Query - Circular-query using Introspection (Denial of Service - /graphql)
[MEDIUM] POST based url-encoded query (possible CSRF) - GraphQL accepts non-JSON queries over POST (Possible Cross Site Request Forgery - /graphql)
```
