---
title: Modules &raquo; m_spanningtree &raquo; Commands &raquo; SVSNICK
layout: default
---

Syntax:

`:<source> SVSNICK <target> <new nickname> <timestamp>`

Asks the server of `<target>` (which must be a UUID) to change the nick of `<target>` to `<new nickname>` with nick timestamp `<timestamp>`.
The `<new nickname>` parameter must either be a nickname or must be the same as '<target>' (which will change the nick of the user to his UUID).

Please note that this is a request, the nick change does NOT happen until the target server reacts with a `NICK` command.
Servers between you and the target server do nothing but simply forward the message in the right direction.

The target server is allowed to kill its user instead of changing his nickname (happens if the change is denied by a module).


PLEASE NOTE: When using this command, it does not in itself force a nickchange at each server directly that it passes through. The server where the old nickname resides is the only server to directly act upon the SVSNICK, and does so by echoing back a NICK to the rest of the network 'acknowledging' the nickchange. Any other servers where the old nick is not a local user will just pass the SVSNICK on, so long as the old nick exists. This allows for services servers to wait for confirmation that the user changed nick, or collided, before actually introducing enforcers. 

Source:
Can be UUID/SID

Routing:
Unicast to the server of `<target>`
