---
title: Modules &raquo; m_spanningtree &raquo; Commands &raquo; IJOIN
layout: default
---

2.0
Not available, send an FJOIN

2.2

Syntax:
`:<uuid> IJOIN <channel> [<channel timestamp> [<prefix mode letters>]]`

Join source user to the given channel only if the channel exists and optionally set modes on the user.
If the channel doesn't exist, the channel is *not* created and the message is *not forwarded*, instead a `RESYNC` (TODO: link) is sent back to the source TODO LINK TO DROPPING COMMANDS
If the channel existss, then the user is joined to the channel. If the second and third parameters are non-empty, the timestamp of the channel is first compared against <channel timestamp>. Then, if the timestamps are equal, all modes listed in <prefix mode letters> are set on the user on the channel.
InspIRCd currently allows and forwards IJOINs with 2 parameters, that is, without modes.

`<prefix mode letters>` can be "o", "ov" or even "hoqav". The order doesn't matter, however, all mode letters must be valid (known) prefix modes.
Source:
Always UUID

Routing:
Broadcast