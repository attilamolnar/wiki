---
title: Modules &raquo; m_spanningtree &raquo; Commands &raquo; PING
layout: default
---

Syntax:

2.0 (Protocol version 1202)
`:<source> PING <source> <destination>`

2.2
`:<source> PING <destination> [<cookie>]`

Request a PONG from server `<destination>`, which does not need to be directly connected
In 2.2, <destination> must be a SID. (TODO: link). If the `<cookie>` parameter exists, it is sent back in the reply (`PONG`)

Routing:
Unicast to <destination>