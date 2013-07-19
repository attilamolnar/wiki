---
title: Modules &raquo; m_spanningtree &raquo; Commands &raquo; SQUIT
layout: default
---

Syntax:

`:<source> SQUIT <quitting server> [<message>]`

Indicates that `<quitting server>` has disconnected from `<source>`.
All users on and behind `<quitting server>` must be removed, `QUIT` messages for those users must not be sent
If the `<message>` parameter exists, it is a user friendly message that describes the reason for the netsplit. Nothing else should be assumed about the contents of that parameter (i.e. its format, exact wording, etc. may change anytime)

Please note that the command for "make server A disconnect from server B" is `RSQUIT` in the InspIRCd protocol, `SQUIT` is only used for telling servers that a server has already quit

Also, the command sent to and expected from directly connected servers to communicate "I'm closing the link with you because ..." is `ERROR`.

Source:
Server only

Routing:
Broadcast
