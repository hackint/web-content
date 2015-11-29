## Frequently Asked Questions

### What is hackint?

hackint is a communication network for the hacker community, but everyone is welcome to use the network.

We support SSL encryption client to server; servers use SSL to communicate with each other.

### How can I run a completely unregulated (opless) channel?

There are two possibilities.

You can either register the channel and remove the autoop (-O) flag from every user. This way, however, some users will still have more control over the channel than others, namely the ones on the channel's access list.

Instead of registering the channel, you can remove your chanop flag immediately after joining the channel. You will never be able to regain chanop status unless you get everyone in the channel to leave.

If you do not immediately deop yourself in the channel, ChanFix will take note of the fact and automatically reop some people if the channel becomes opless. You cannot turn a channel with chanops into an opless channel, unless you register it with ChanServ.

### What does "can't join channel #foo (+S)" mean?

It means that you need to connect to the network via SSL.

### I can't connect to the network - can you help?

If you are unable to connect to the hackint IRC network, check the error message you get when you try to connect. Please use the e-mail address specified in the error message (if any) to get in touch with us.

### Can I register my nickname/channel?

Yes. To register your nickname, enter /msg nickserv help register and follow the instructions given there. You need not specify a valid email address. The email address is required only if you forget your nickserv password (but passwords are obsolete anyway; you can identify via an ssl client certificate). To register your channel, you need a registered nickname. Then, enter /msg chanserv help register and follow the instructions.

### What kind of channels are allowed on hackint? Is there some kind of on-topic/off-topic policy?

You are welcome to create any kind of channel, as long as it does not violate German, French and/or US law (the three countries in which you will find hackint servers).

### Someone has taken over my nick/channel, can you help?

I'm sorry, no; that's what NickServ, ChanServ and GroupServ are here for.

### Do nicks expire on hackint?

They do, after 365 days of inactivity.

### $(NICK) has been unused for a while, can I have it?

Nicks expire after 365 days of inactivity. However, if a nick has not been used for a while, we might to decide to drop it earlier based on various non-disclosed factors. Just join #hackint and ask. Note that nicks will never be dropped if unused for 12 weeks or less.

### How do I report abusive behavior?

Just join #hackint and talk to us there.

### Can I get a vhost/cloak?

Yes, you can. If you're identified with NickServ, do the following:

/msg hostserv take hackint/user/$account

Do not replace $account with your account name. Services will automatically substitute it with your account name.

If you want anonymity, please use Tor or i2p to connect to hackint.
I have a question that is not answered here.

Join #hackint and ask talk to us there.

### What is the greasel?

The greasel is head of hackint's security team. It was bred in hackint's oceanic laboratories with generous support from Page industries.
