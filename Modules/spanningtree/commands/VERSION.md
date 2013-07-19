---
title: Modules &raquo; m_spanningtree &raquo; Commands &raquo; VERSION
layout: default
---

Syntax:
`:<sid> VERSION <version string>`

Announces that the server version string of `<sid>` is `<version string>`.

`<version string>` may be an arbitrary string, no assumptions should be made about the format of version strings.

`VERSION` commands are sent as part of the network burst.
All servers then cache the version strings of all other connected servers and may return them to clients without making any requests to the network. Servers may also update their version strings at any point after the burst.

There is no such thing as a "version request" in the InspIRCd protocol.

Source:
Only server

Routing:
Broadcast