---
title: Modules &raquo; m_spanningtree &raquo; Commands &raquo; IDLE
layout: default
---

Syntax:
`:<source> IDLE <target> [<signon time> <idle seconds>]`

Request or reply the idle information of a user.
Request form: only the `<target>` parameter is present, `<source>` is the requesting user, target is the user whose idle information is queried.
Reply form: all three parameters are present, target is the user who requested the information (i.e. the `<source>` in the request form), <signon time> is a timestamp when the user has logged on, <idle seconds> is the number of seconds this user has been idle

Source:
Always UUID

Routing:
Unicast to the server of <target>, dropped if <target> is a valid but non-existant uuid.