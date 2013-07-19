---
title: Modules &raquo; m_spanningtree &raquo; Commands &raquo; METADATA
layout: default
---

2.0

Syntax:
`:<sid> METADATA <target> <extension name> [<extension data>]`

Set/exchange extension data
`<target>` can be a UUID (user `METADATA`), a channel (channel `METADATA`) or `*` (server `METADATA`).

2.2
Syntax:
User/server:
`:<sid> METADATA <target> <extension name> [<extension data>]`

Channel:
`:<sid> METADATA <channel> <channel timestamp> <extension name> [<extension data>]`

The timestamp of the channel is compared `<channel timestamp>`. If they don't match, the command is dropped. TODO LINK TO DROPPING COMMANDS

Most non-InspIRCd systems can safely ignore METADATA commands (and should do so!), and should NOT send any without knowing exactly which module uses the given key, and what for, and the format of their serialized data. Please note that the <value> field only has to be meaningful to the module which generated the message, and may not be usable in any other form (e.g. it may be encrypted or otherwise munged).

Source:
Always SID

Routing:
Broadcast