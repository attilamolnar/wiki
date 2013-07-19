---
title: Modules &raquo; m_spanningtree &raquo; Commands &raquo; OPERTYPE
layout: default
---

Syntax:
`:<uuid> OPERTYPE <type>`

Indicates that the `<uuid>` is now an IRC operator of type `<type>`
The given type doesn't need to exist on all servers, it is used for WHOIS replies.
This command automatically sets the usermode +o on the client, setting usermode +o via other means is not allowed

Source:
Always UUID

Routing:
Broadcast