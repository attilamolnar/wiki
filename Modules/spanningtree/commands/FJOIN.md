---
title: Modules &raquo; m_spanningtree &raquo; Commands &raquo; FJOIN
layout: default
---

Syntax:
`:<sid> FJOIN <channel> <timestamp> <modes> [<mode parameters> ...] <userlist>`

Format of `<userlist>`:
`[<userlist entry> [<userlist entry> [ ... ]]]`

Format of `<userlist entry>`
`<mode letters>,<uuid>`

`<mode letters>` are prefix mode letters, such as "o" or "ovh", or "" (nothing).

Join users to a channel and set modes on it, creating it if it doesn't exist.

If the channel doesn't exist it is first created with the timestamp `<timestamp>`.

The channel timestamp is compared against `<timestamp>`.

If `<timestamp>` is older (smaller) the following happens:
- All modes are removed from the channel (simple modes, listmodes, prefix modes, everything)
- All metadata associated with the channel is unset
- Topic is unset
- Channel timestamp is set to `<timestamp>`
- The channel name is set to `<channel>` (so if the names differ in case, the remote is kept)
- `<modes>` are set on the channel
- All users in `<userlist>` are joined to the channel and the given modes are set on them

If '<timestamp>' is equal to the timestamp of the channel, the following happens:
- `<modes>` are merged (TODO LINK MODE MERGING)
- All users in `<userlist>` are joined to the channel and the given modes are set on them

If '<timestamp>' is newer (bigger) than the timestamp of the channel, the following happens:
- `<modes>` are IGNORED
- All users in `<userlist>` are joined to the channel, the given modes are IGNORED

In all 3 scenarios, no new server to server messages are generated and the `FJOIN` command is passed on verbatim.

Channel restrictions on users should be ignored to prevent desyncs, e.g. bans, invite exceptions, keys and invite-only status should not be checked for joining users.

This command is used within a netburst to synchronize all of the users on a channel, and set their permissions upon that channel.

Please note that an empty (but existant) `<userlist>` is allowed, (think of empty permanent channels).

Examples:

`:003 FJOIN #c 11111 +kl secret 20 :,003AAAAAA aqohv,003AAAAAC o,003AAAAAB`
Modes requiring parameters and three users, one of them is a channel op, another one has +aqohv, third has no prefix modes

`:0DD FJOIN #chan 1234 +CJfjnt 10 8:6 8:6 ,0DDAAAAFE`
Even more modes that require parameters and a single user without prefix modes

`:497 FJOIN #smelly 12345 +nt :oh,497AAAAAB ,497AAAAQZ h,497AAART0 ,497AAAZZ6 a,497AAYU9B oX,497AAB67L`

If a server ever receives a mode which it does not recognize, for example the X in the example above, it should immediately close the connection (after sending an ERROR message) to prevent a desync.
This situation indicates that modules are not configured identically on both sides of the network, and continuing to link the servers could cause problems.
Services may relax this restriction somewhat, however it should be noted that they may not know what functionality a mode allows users - and therefore MUST be careful what restrictions they impose on a user with an unknown mode.

`:650 FJOIN #permchan 222222 +P :`
Empty permanent channel, with only the permanent channel mode (`+P`) set on it. Note that the last parameter is not entirely omitted, but is an empty string.

Source:
Always SID

Routing:
Broadcast