---
title: Modules &raquo; m_spanningtree &raquo; Commands &raquo; RESYNC
layout: default
---

Syntax:

2.0
Not available

2.2
`:<sid> RESYNC <channel>`

Request the resynchronization of `<channel>`.
The receiving server will reply with a series of `FJOIN`, `FMODE`, `FTOPIC` and `METADATA` messages for the given channel that contain all channel information

Routing:
Direct only