---
title: Modules &raquo; m_spanningtree &raquo; Commands &raquo; SVSJOIN
layout: default
---

Syntax:

`:<source> SVSJOIN <target> <channel>`

Asks the server of `<target>` (which must be a UUID) to join the target user to channel `<channel>`.
The given channel doesn't need to exist.

Please note that this is a request, the actual join happens when (if) the target server reacts with an appropiate message.
Servers between you and the target server do nothing but simply forward the message in the right direction.

Source:
Can be UUID/SID

Routing:
Unicast to the server of `<target>`
