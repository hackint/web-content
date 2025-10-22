# Transport / Matrix

| Portal rooms              | Host-Cloak          |
|---------------------------|---------------------|
| #yourchannel:hackint.org  | fd1a:6295:5133::/64 |

## Retention

We apply a retention policy on events, so that we don't hold data beyond 7 days.

Media content shared from the Matrix will be served for up to 90 days from our homeserver.

## Known issues

- Conversations with the Appservice and NickServ happen in plain text, which means sending your password over the bridge will store it on your homeserver, where different retention policies may apply.

## Frequently Asked Questions

### Account registration and automatic login

Users joining us from Matrix can make use of NickServ accounts to protect their
name and maintain ACLs for Channels using ChanServ. To achieve that open a
conversation with both `@appservice-irc:hackint.org` and make sure you've set
the IRC nickname you desire.

```
!nick <name>
```

Then open a conversation with `@NickServ:hackint.org` and complete the
registration flow, by passing your email address and a unique account password
to the `register` command. We will send you an email to confirm your address,
it holds a token that you need to pass to `@NickServ:hackint.org` to complete
your registration.

```
register <password> <email>
verify register <name> <token>
```

Then return to the conversation with `@appservice-irc:hackint.org` to store
your credentials, to be automatically logged in on connect. Follow up by
reconnecting the IRC session to make sure you are being logged in, which
NickServ will confirm in your conversation.

```
!username <name>
!storepass <password>
!reconnect
```

The given password has to be stored in plaintext on our matrix infrastructure
so it can be used during connection attemps to authenticate with our services.
Please make sure to use a *unique* password.


### Bridging with existing Matrix rooms (Plumbing)

On a case by case basis we can provide plumbing to your existing Matrix room
into one of hackints IRC rooms. Plumbing can only be requested by users that
are operators (ChanServ permissions) to the IRC channel in question.

To initiate the plumbing process, start by inviting
`@appservice-irc:hackint.org` into your Matrix room and equip them with a PL
(we recommed a PL 50>x<100) that can promote useres to moderator. This is
required for permission mapping between IRC (+o/+v) and Matrix (PL50/1) can
take place.
The appservice will only join the room, once the plumbing process is complete.

When you have completed these steps contact us in `#hackint` and provide us
with the raw MXID (`!randomstring:example.com`) to your channel as well as the
IRC room on hackint you would like bridged to it.

### What if I don't want Matrix users in my channel?

Preventing matrix users from joining your rooms can be achieved by banning
the prefix we hand out to Matrix users.

```
/mode +b *@fd1a:6295:5133::/64
```

### Administrating the bridged Matrix room

The bridged room on Matrix has its own room settings, such as for example
privacy settings or the channel logo.

These settings can be modified by Matrix bridge users which are identified
with NickServ and have channel operator permissions on the IRC side.
