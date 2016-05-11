## User Modes (*umodes*)

User modes affect certain settings between you and the IRC Daemon, like how much information you will receive from the ircd or how easy it will be to find you. They're commonly refered to as *umodes*.

```
MODE <nick> <+|-><modes>

User modes: (* designates that the umode is oper only)
            (? designates that the umode is provided by an extension
             and may not be present on this server)

     USERMODE     DESCRIPTION
-----------------------------------------------------------------
         +i     - Designates this client 'invisible'.
         +g     - "caller id" mode only allow accept clients to message you
         +w     - Can see oper and server wallops.
       ? +h     - Has a cloaked host. May be +x depending on cloaking module
         +o     - Designates this client is an IRC Operator.
                  Use the /oper command to attain this.
       * +a     - Is marked as a server admin in whois.
       * +l     - Can see oper locops (local wallops).
       * +s     - Can see server notices (see /quote help snomask).
       * +z     - Can see operwalls.
         +D     - Deaf - ignores all channel messages.
         +Q     - Prevents you from being affected by channel forwarding.
         +R     - Prevents unidentified users that you have not accepted from
                  messaging you.
         +Z     - Is connected via SSL (cannot be set or unset).
```
