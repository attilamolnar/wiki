---
title: Modules &raquo; m_spanningtree &raquo; Commands &raquo; BURST
layout: default
---

Syntax:
`:<sid> BURST [<current timestamp>]`

Indicates that server `<sid>` has started bursting.
InspIRCd makes a distinction between bursting and non-bursting servers, see <performance:quietbursts>.

You must send this command before you commence netburst, see bursting. (TODO: LINK HERE)

If the <current timestamp> parameter is given, it is compared to the current timestamp on the receiving server and the link is aborted if the difference is deemed to be too much. Remote servers do not check this parameter.

Source:
Only SID

Routing:
Broadcast