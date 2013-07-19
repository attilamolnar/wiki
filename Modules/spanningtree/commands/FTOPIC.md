---
title: Modules &raquo; m_spanningtree &raquo; Commands &raquo; FTOPIC
layout: default
---

Syntax:

2.0 (Protocol version 1202)
`:<source> FTOPIC <channel> <topic timestamp> <topic setter> <topic>`

2.2
`:<source> FTOPIC <channel> <channel timestamp> <topic timestamp> <topic setter> <topic>`

Burst (or change) topic on a channel. The topic is updated only if the current topic timestamp is older than `<topic timestamp>`. In other words, newer topics override older topics.

In 2.2 the `<channel timestamp>` is checked first, and if it's newer than the current timestamp of the channel, the command is dropped. TODO LINK TO DROPPING COMMANDS
If both topic timestamps are equal, the alphabetically smaller topic is discarded.

Routing:
Broadcast