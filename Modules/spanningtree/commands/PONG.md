---
title: Modules &raquo; m_spanningtree &raquo; Commands &raquo; PONG
layout: default
---

Syntax:

2.0 (Protocol version 1202)
`:<source> PONG <source> <destination>`

2.2
`:<source> PONG <destination> [<cookie>]`

Reply to a `PING` from server `<destination>`, which does not need to be directly connected
In 2.2, <destination> must be a SID. (TODO: link). If the `<cookie>` parameter was present in the `PING` message, it is sent back exactly as received as the last parameter

Routing:
Unicast to <destination>