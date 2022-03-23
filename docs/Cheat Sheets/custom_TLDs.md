---
tags: [dns]
---
# Custom TLDs

Challenge platforms often use local domains with custom TLDs to access machines
that have a dynamic IP address.
Eg. `box.htb` on HackTheBox or `room.thm` on TryHackMe.

Some custom TLDs are also used internally on corporate environment such as
`.local`, `.home`, `.lan`, `.corp`, `.intra` or even the name of your company used
as TLD.

The issue is that only those 4 are standard: `.test`, `.localhost`, `.invalid`, `.example`.
So other private TLDs are considered non-standard (custom) and won't be recognized
by web browsers.
That's not very annoying since putting a full URL in you browser search bar will
work. But when the protocol (eg. `http://`, `https://`, `ftp://`) is omitted, when
you provide only the domain (eg. `corpowiki.lan` and not `https://corpowiki.lan`),
you will end up querying on your default search engine instead of reaching that
internal private domain. That is annoying.

To prevent this behavior and register your custom TLD as if it was a public
standard TLD, you can tweak options on your web browser.

!!!primary Info
Mozilla Firefox recognize `.internal` and `.local` in addition to the 4 reserved
domains (`.test`, `.localhost`, `.invalid`, `.example`).
!!!

For Mozilla Firefox:

1. Reach the advanced setting page: `about:config`
2. Add a boolean key for your custom TLD: `browser.fixup.domainsuffixwhitelist.<myTLD>` eg. `browser.fixup.domainsuffixwhitelist.htb`

![](https://i.imgur.com/HmrEECo.png)

Unfortunately this feature doesn't ([and will never](https://bugs.chromium.org/p/chromium/issues/detail?id=30636))
exist for Chromium / Google Chrome users. But there is a trick to define a pseudo
search engine. Example with `.htb`.

1. Go to `chrome://settings/searchEngines`
2. `Add` a new search engine
3. Fill the 3 fields as follow:
  - Search engine: `HackTheBox`
  - Keyword: `htb`
  - URL with %s in place of query: `http://%s.htb`

![](https://i.imgur.com/2vIXl1E.png)

Then typing your keyword followed by a space followed by the domain will form
the searched FQDN, eg. `HTB` + <kdb>SPACE</kdb> + `noraj` will search `http://noraj.htb`.

![](https://i.imgur.com/P6SmPQH.png)

See also:

- [SAC113 - SSAC Advisory on Private-Use TLDs](https://www.icann.org/en/system/files/files/sac-113-en.pdf)
- [RFC2606 - Reserved Top Level Domain Names](https://datatracker.ietf.org/doc/html/rfc2606)
- [RFC6761 - Special-Use Domain Names](https://datatracker.ietf.org/doc/html/rfc6761)
- [RFC6762 - Multicast DNS - Appendix G. Private DNS Namespaces](https://datatracker.ietf.org/doc/html/rfc6762#appendix-G)

