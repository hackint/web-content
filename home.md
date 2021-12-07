# Welcome to hackint!

hackint is a communication network for the [hacker](https://en.wikipedia.org/wiki/Hacker_culture) community, but anyone is welcome to use its services. We are fully [ircv3.1](http://ircv3.net/irc/#ircv31) and partially [ircv3.2](https://ircv3.net/irc/#ircv32) compliant.

## News

### 2021/12/07 Matrix support is returning to hackint

tl;dr: Join rooms on hackint.org from Matrix via `#channel:hackint.org`. Say hello from Matrix in [#hackint:hackint.org (for #hackint)](https://matrix.to/#/#hackint:hackint.org)!

Back in 2018 we did announce the [sunsetting of the matrix bridge](https://hackint.org/archive#20181028_Matrix_Bridging_Sunset). Back then our primary points of concern were:

1. memory intensiveness
2. excessive logging to database, even though we're only relaying information
3. clients are occasionaly not properly rejoined, but might be able to read messages nevertheless user connections are never culled, even when they become unused

In the last couple of years we've tested the bridge in multiple rounds in regards to these issues. Over the course of that time the bridge Matrix ecosystem and the bridge code has improved a lot. Especially on the Matrix side there have been huge improvements in terms of memory and cpu consumption as well as retention policies. We'd like to take the time to address each of these points and why we think that we are now able to provide a bridging setup again.

On memory intensiveness: Earlier this year the Synapse team put a lot of effort into reducing the memory consumption of Synapse. The requirements to join large channels has since dropped significantly and we haven't seen a lof of memory (or CPU) usage on regular (fairly busy) homeservers. That being said, the matrix bridge is likely the single most busy server that hackint operates. :)

On logging & database growth: Around the time of our sunsetting the Matrix team started the discussion on [message rention (MSC1763)](https://github.com/matrix-org/matrix-doc/pull/1763#issuecomment-450530676). Since then synapse gained support for purging messages based on configurable schedules. We will purge messages (and media) rather agressively and not store it for extended periods of time. This means that we will only backfill history to users that were joined within an hour of a conversation happening, and even that is conditional on a channels privacy settings. This should cover most network segmentations while keeping the data on our servers limited. A note on media: Even if media has already been purged from our services it can (and will) be retrieved from the origin server again when requested.

Last but not least the actual IRC bridge problems: The IRC bridge hasn't seen much love for the last couple of years *until* the Freenode accident happened. The Matrix team was very eager to provide Matrix bridging to Freenode's spiritual successor [Libera.Chat](https://libera.chat) and [they started discussing](https://twitter.com/liberachat/status/1396920289641091079) their concerns! This has led to fixes for most of our long-standing gripes with the bridge. You can read more about this in [This Week in Matrix 2021-06-18 matrix-appservice-irc notes](https://matrix.org/blog/2021/06/18/this-week-in-matrix-2021-06-18#matrix-appservice-irc-weights-in-at-release-0270) and the related GitHub issues, conversations etc..

Do we think it is perfect? We wouldn't say so. It is a long way away. You will certainly see issues but the overall experience isn't as rocky as it used to be. This is why we feel confident enough to offer the bridge again.


#### Account registration and automatic login

Users joining us from Matrix can make use of NickServ accounts to protect their name and maintain ACLs for Channels using ChanServ. To achieve that open a conversation with both `@appservice-irc:hackint.org` and make sure you've set the IRC nickname you desire.

```
!nick <name>
```

Then open a conversation with `@NickServ:hackint.org` and complete the registration flow, by passing your email address and a unique account password to the `register` command. We will send you an email to confirm your address, it holds a token that you need to pass to `@NickServ:hackint.org` to complete your registration.

```
register <email> <password>
verify <token>
```

Then return to the conversation with `@appservice-irc:hackint.org` to store your credentials, to be automatically logged in on connect. Follow up by reconnecting the IRC session to make sure you are being logged in, which NickServ will confirm in your conversation.

```
!username <name>
!storepass <password>
!reconnect
```

The given password has to be stored in plaintext on our matrix infrastructure so it can be used during connection attemps to authenticate with our services. Please make sure to use a *unique* password.


#### Bridging with existing Matrix rooms (Plumbing)

On a case by case basis we can provide plumbing to your existing Matrix room into one of hackints IRC rooms. Plumbing can only be requested by users that are operators (ChanServ permissions) to the IRC channel in question.

To initiate the plumbing process, start by inviting `@appservice-irc:hackint.org` into your Matrix room and equip them with admin permissions to the room. The appservice will only join the room, when the plumbing process is complete. This is a prerequisite for the plumbing process to work.

When you have completed these steps contact us in `#hackint` and provide us with the raw MXID (`!randomstring:example.com`) to your channel as well as the IRC room on hackint you would like bridged to it.

#### What if I don't want Matrix users in my channel?

Preventing matrix users from joining your rooms can be achieved by banning `*@gateway/matrix*` from your channel.

```
/mode +b *@gateway/matrix*
```

The trailing wildcard is recommended, as we intend to equip Matrix users with individual hostnames in the future.


### 2020/03/01 TLS1.3 is here!

Heads up! We're going TLS1.3 during this month. The first machine has already been upgraded today and everything looks good.

- If your clients supports TLS1.3 (or TLS1.2) you don't need to do anything, you will be able to reconnect without reconfiguration.
- If you're however running on an older system, please note that we disable support TLS1.0 and TLS1.1 in this change.

## News Archive

Older news can be found in the [archive](/archive).
