---
title: Modules &raquo; m_spanningtree &raquo; Commands &raquo; SERVER
layout: default
---

Syntax:

When handshaking:
`SERVER <server name> <password> <reserved> <sid> <description>`

After handshake (introducing a server behind the sender)
`:<source> SERVER <server name> * <reserved> <sid> <description>`

When handshaking, tell the remote server about our identity.

Post-handshake, it is used to introduce new servers to the network. In this case, the new server is assumed to be directly connected to server `<source>`.
Note that passwords are never sent 

In both cases if server name `<server name>` or SID `<sid>` already exists somewhere on the network, the link is aborted.

No assumptions should be made about the contents of the `<reserved>` parameter.

Source:
Server only

Routing:
Broadcast
