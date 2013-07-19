---
title: Modules &raquo; m_spanningtree &raquo; Commands &raquo; OPERQUIT
layout: default
---

Syntax:
`:<uuid> OPERQUIT <message>`

Indicates that the oper-only quit message of `<uuid>` has changed to `<message>`.

This command is used to specify a quit message for a user which only opers see, which is seperate from the message sent by the normal QUIT command. This is used for example by GLINEs with the <options:hidebans> option enabled. Modules may also use this to cause a different message to be displayed for opers than for normal users for any particular user quit. 
IMPORTANT NOTE: The OPERQUIT command does not actually cause the user to quit. It simply causes the message given to be stored within the user's structure, for the time when they do quit with the normal QUIT command, at which point this message is sent to opers and the message sent by QUIT is sent to everyone else. Services may or may not choose to store and make use of the seperate oper quit message, depending on its design.

Source:
Always UUID

Routing:
Broadcast