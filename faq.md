# Frequently Asked Questions

## General

### What is hackint?

hackint is a Internet Relay Chat network for the hacker community worldwide, however everyone is welcome to use this service.

### I can't connect to the network - can you help?

If you are unable to connect to the hackint IRC network, check the error message you get when you try to connect. Please use the e-mail address specified in the error message (if any) to get in touch with us.

### Can I register my nickname?

Yes. To register your nickname, enter

```
/msg nickserv help register
```

and follow the instructions given there. A valid email address is required in case you forget your NickServ password. Email confirmation may be required during phases of high abuse.


### Can I regsiter a channel?

To register your channel, you first need to register and identify for a  nickname. Then, enter

```
/msg chanserv help register
```

and follow the instructions.

### What kind of channels are allowed on hackint? Is there some kind of on-topic/off-topic policy?

You are welcome to create any kind of channel, as long as it does not violate German or Dutch law.

### Someone has taken over my nick/channel, can you help?

We're sorry, no; that's why you should make use of NickServ, ChanServ and GroupServ.

### Do nicks expire on hackint?

They do, after 365 days of inactivity.

### $(NICK) has been unused for a while, can I have it?

Nicks expire after 365 days of inactivity. However, if a nick has not been used for a while, we might to decide to drop it earlier based on various non-disclosed factors. Just join [#hackint](ircs://irc.hackint.org/hackint) and ask. Note that nicks will never be dropped if unused for 12 weeks or less.

### How do I report abusive behavior?

Just join [#hackint](ircs://irc.hackint.org/hackint) and talk to us there.

### Can I get a vhost/cloak/spoof?

Yes, you can. If you're identified with NickServ, do the following:

```
/msg hostserv take hackint/user/$account
```

Do not replace `$account` with your account name. Services will automatically substitute it with your account name.

**However:** If you want real anonymity, please use the Tor hidden services to connnect to hackint.

### How can I run a completely unregulated (opless) channel?

There are two possibilities.

1. You can either register the channel and remove the autoop (-O) flag from every user. This way, however, some users will still have more control over the channel than others, namely the ones on the channel's access list.

2. Instead of registering the channel, you can remove your chanop flag immediately after joining the channel. You will never be able to regain chanop status unless you get everyone in the channel to leave.

 If you do not immediately deop yourself in the channel, ChanFix will take note of the fact and automatically reop some people if the channel becomes opless. You cannot turn a channel with chanops into an opless channel, unless you register it with ChanServ.

### I have a question that is not answered here.

Join [#hackint](ircs://irc.hackint.org/hackint) and ask your question there.
