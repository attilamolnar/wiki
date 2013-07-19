---
title: Modules &raquo; m_spanningtree &raquo; Commands &raquo; SAVE
layout: default
---

Syntax:

`:<sid> SAVE <target> <timestamp>`

Force nick change of `<target>` (must be a UUID) to UUID, if <timestamp> matches the nick timestamp of `<target>`

Source:
SID only

Routing:
When received: Broadcast
When generated locally: Sent only to the source of the `UID` command that triggered the collission (see Nickname collission) TODO LINK