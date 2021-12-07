# Transport / Matrix

| Portal rooms              | Host-Cloak       |
|---------------------------|------------------|
| #yourchannel:hackint.org  | gateway/matrix/* |

We are currently in a closed testing phase, and a very limited subset of channels was bridged. If you want to participate testing you can join `#hackint-matrix:hackint.org`.

## Retention

Hackint implements a rigorous retention policy, so that we do not store conversations older than two minutes. As such we do not participate in providing backlog to remote users, unless they were present at the time, when an event first occured. Other homeservers will likely fill the gap, should your channel have a more relaxed setting concerning history.

Media content shared from the Matrix side will be served up to 90 days via our homeserver.

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
register <email> <password>
verify <token>
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
`@appservice-irc:hackint.org` into your Matrix room and equip them with admin
permissions to the room. The appservice will only join the room, when the
plumbing process is complete. This is a prerequisite for the plumbing process
to work.

When you have completed these steps contact us in `#hackint` and provide us
with the raw MXID (`!randomstring:example.com`) to your channel as well as the
IRC room on hackint you would like bridged to it.

### What if I don't want Matrix users in my channel?

Preventing matrix users from joining your rooms can be achieved by banning
`*@gateway/matrix*` from your channel.

```
/mode +b *@gateway/matrix*
```

The trailing wildcard is recommended, as we intend to equip Matrix users with
individual hostnames in the future.
