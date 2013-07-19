---
title: Modules &raquo; m_spanningtree &raquo; Commands &raquo; FMODE
layout: default
---

Syntax:
`:<source> FMODE <channel> <timestamp> <modes> [<mode parameters> ...]`

Change modes on `<channel>`.
If the given `<timestamp>` is newer than the current timestamp of the channel, the modes are not applied and the command is dropped (TODO: LINK TO WHAT IS DROPPED)

2.0

If `<source>` is a sid, then modes are merged. TODO LINK TO MODE MERGE
All nicknames in the mode change must be sent as UUIDs.

Source:
SID or UUID

Routing:
Broadcast