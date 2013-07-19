---
title: Modules &raquo; m_spanningtree &raquo; Commands &raquo; AWAY
layout: default
---

Syntax:
`:<uuid> AWAY [<timestamp> <away reason>]`

Marks the source '<uuid>' as away (if parameters exist) or back from away (no parameter version).
The '<timestamp>' field is the time when the user marked themselves as away.

This message is sent at burst for each user that is away.

Routing:
Broadcast