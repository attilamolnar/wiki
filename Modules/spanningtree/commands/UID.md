---
title: Modules &raquo; m_spanningtree &raquo; Commands &raquo; NICK
layout: default
---

Syntax:
`:<sid> UID <uuid> <nick timestamp> <nick> <real hostname> <displayed hostname> <ident> <ip> <signon time> +<modes> [<mode params> ...] <gecos>`

Introduce a new client into the network.
If there is a nickname collission then the usual Nickname collission (TODO LINK) rules apply. If the remote side loses then the `<nick>` parameter of this message is set to the value of `<uuid>` before the command is propagated

The `<ip>` field is in dotted decimal form for IPv4 addresses, e.g. `1.2.3.4`, or colon-seperated hex digits for IPv6, such as `dead:beef:3030:4343:b00b:c0ca:c01a`. It is important to note that an IPv6 address cannot start with `:`, and if it would normally start with a `:` due to compression of addresses (omitting of 0 fields) then a `0` prefix must be added, e.g. `0::ffff:1234:5678`.

It is important to note that after the <modes> parameter there may be one or more space separated values, dependent upon whether any of the modes given in the sequence require parameters (such as +s for snomasks). If this is the case, there may be more than ten parameters to the UID command (such as when snomasks are set). The GECOS will always be the final parameter and should always be accessible through parameters[numberofparams-1] in whatever array is used to represent the parameters of the command.

Source:
Always SID

Routing:
Broadcast