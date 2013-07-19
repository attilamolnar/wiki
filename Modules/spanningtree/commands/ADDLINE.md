---
title: Modules &raquo; m_spanningtree &raquo; Commands &raquo; ADDLINE
layout: default
---

Syntax:
`:<source> ADDLINE <type> <mask> <setter> <set timestamp> <duration> <reason>`

This command is used to set an XLine.
The setter can be any arbitrary text up to 64 characters in length (so it may be a nick which is not online, or a server name which no longer exists).
The line `<type>` must be a recognized XLine to the rest of the network, supported by a loaded module or the core.

The core of InspIRCd supports and recognises the following line types (case sensitive):
- G - GLINE
- Z - ZLINE
- E - ELINE
- Q - QLINE
- K - KLINE 

The `<mask>` is specific to the module implementing the XLine.

Servers must use this command to sync Q, Z, E, G and other lines during and after a burst.

Setting XLines using the commands `GLINE`, `ZLINE`, `SHUN`, etc. is NOT SUPPORTED!
TODO: LINK

Source:
Only server

Routing:
Broadcast