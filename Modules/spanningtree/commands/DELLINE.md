---
title: Modules &raquo; m_spanningtree &raquo; Commands &raquo; DELLINE
layout: default
---

Syntax:
`:<source> DELLINE <type> <mask>`

Removes XLine `<mask>` of type `<type>`.

The line type must be a recognized XLine to the rest of the network, supported by a loaded module or the core. See the `ADDLINE` command for a list of core recognized line types.

The `<mask>` is specific to the module implementing the XLine.

Source:
Only server

Routing:
Broadcast