---
title: Modules &raquo; m_spanningtree &raquo; Commands &raquo; SVSPART
layout: default
---

Syntax:

`:<source> SVSPART <target> <channel>`

Asks the server of `<target>` (which must be a UUID) to part the target user from channel `<channel>`.
If the given channel doesn't exist, the command is silently dropped.

Please note that this is a request, the actual PART happens when the target server reacts with a PART message
Servers between you and the target server do nothing but simply forward the message in the right direction.

Source:
Can be UUID/SID

Routing:
Unicast to the server of `<target>`
