---
title: Modules &raquo; m_spanningtree &raquo; Protocol
layout: default
---

## Introduction to the Spanning Tree Protocol

InspIRCd's protocol is a UID/SID based protocol similar in behaviour to the [TS6 protocol](http://hg.atheme.org/charybdis/file/tip/doc/technical/ts6-protocol.txt)
used by some other IRC servers. Linking a server using the InspIRCd Spanning Tree Protocol is
relatively straightforward for anyone who's handled IRC servers and their protocols before.

Protocol changes will be generally backwards-compatible with previous major versions. Major version
changes (e.g. 1.1 to 1.2) usually mean major protocol changes. Any changes to the protocol in minor
releases will not usually break previous releases unless absolutely necessary (e.g. to fix an
exploit or race condition).

Please note that the InspIRCd Spanning Tree Protocol is not related in any way to the CISCO
Spanning Tree Protocol used in local area networks. The name of our protocol comes from the
mathematical name for the tree structure it represents, similar to the reason for their naming.

## Protocol Documentation

Due to the advanced and detailed nature of the InspIRCd Spanning Tree Protocol, the documentation is
split into multiple sections for easier searching and readability. Please choose the section you
require from the list below:

* [Connecting a Server](/wiki/Modules/spanningtree/Connecting-a-Server.html)
&mdash; guide to connecting two servers together, authentication mechanisms and handshake protocols.

* [Commands](/wiki/Modules/spanningtree/Commands.html) &mdash;
a list of commands supported by the InspIRCd Spanning Tree Protocol.

* [UUIDs](/wiki/Modules/spanningtree/UUIDs.html) &mdash; a
guide to UUIDs (Universally Unique Identifiers) used to identify users and servers.

* [Nickname Collision Handling](/wiki/Modules/spanningtree/Nickname-Collision-Handling.html)
&mdash; a guide to collision handling and prevention of unnecessary nickname collision kills.

* [Message Routing](/wiki/Modules/spanningtree/Message-Routing.html)
&mdash; a guide to message routing in the InspIRCd Spanning Tree Protocol.

* [Server Types](/wiki/Modules/spanningtree/Server-Types.html)
&mdash; a guide to different types of server in the InspIRCd Spanning Tree Protocol.

* [Timestamp Synchronization](/wiki/Modules/spanningtree/Timestamp-Synchronization.html)
&mdash; a guide to keeping your clocks correct: Important for IRC as a whole.

* [Example Traffic](/wiki/Modules/spanningtree/Example-Traffic.html)
&mdash; an example conversation between two InspIRCd 1.2 servers.
