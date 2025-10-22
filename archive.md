# News Archive

### 2021/12/07 Matrix support is returning to hackint

tl;dr: Join rooms on hackint.org from Matrix via `#channel:hackint.org`. Say hello from Matrix in [#hackint:hackint.org (for #hackint)](https://matrix.to/#/#hackint:hackint.org)!

Back in 2018 we did announce the [sunsetting of the matrix bridge](https://hackint.org/archive#20181028_Matrix_Bridging_Sunset). Back then our primary points of concern were:

1. memory intensiveness
2. excessive logging to database, even though we're only relaying information
3. clients are occasionaly not properly rejoined, but might be able to read messages nevertheless user connections are never culled, even when they become unused

In the last couple of years we've tested the bridge in multiple rounds in regards to these issues. Over the course of that time the bridge Matrix ecosystem and the bridge code has improved a lot. Especially on the Matrix side there have been huge improvements in terms of memory and cpu consumption as well as retention policies. We'd like to take the time to address each of these points and why we think that we are now able to provide a bridging setup again.

On memory intensiveness: Earlier this year the Synapse team put a lot of effort into reducing the memory consumption of Synapse. The requirements to join large channels has since dropped significantly and we haven't seen a lof of memory (or CPU) usage on regular (fairly busy) homeservers. That being said, the matrix bridge is likely the single most busy server that hackint operates. :)

On logging & database growth: Around the time of our sunsetting the Matrix team started the discussion on [message retention (MSC1763)](https://github.com/matrix-org/matrix-doc/pull/1763#issuecomment-450530676). Since then synapse gained support for purging messages based on configurable schedules. We will purge messages (and media) rather agressively and not store it for extended periods of time. This means that we will only backfill history to users that were joined within an hour of a conversation happening, and even that is conditional on a channels privacy settings. This should cover most network segmentations while keeping the data on our servers limited. A note on media: Even if media has already been purged from our services it can (and will) be retrieved from the origin server again when requested.

Last but not least the actual IRC bridge problems: The IRC bridge hasn't seen much love for the last couple of years *until* the Freenode accident happened. The Matrix team was very eager to provide Matrix bridging to Freenode's spiritual successor [Libera.Chat](https://libera.chat) and [they started discussing](https://twitter.com/liberachat/status/1396920289641091079) their concerns! This has led to fixes for most of our long-standing gripes with the bridge. You can read more about this in [This Week in Matrix 2021-06-18 matrix-appservice-irc notes](https://matrix.org/blog/2021/06/18/this-week-in-matrix-2021-06-18#matrix-appservice-irc-weights-in-at-release-0270) and the related GitHub issues, conversations etc..

Do we think it is perfect? We wouldn't say so. It is a long way away. You will certainly see issues but the overall experience isn't as rocky as it used to be. This is why we feel confident enough to offer the bridge again.

### 2020/03/01 TLS1.3 is here!

Heads up! We're going TLS1.3 during this month. The first machine has already been upgraded today and everything looks good.

- If your clients supports TLS1.3 (or TLS1.2) you don't need to do anything, you will be able to reconnect without reconfiguration.
- If you're however running on an older system, please note that we disable support TLS1.0 and TLS1.1 in this change.

### 2018/10/28 CA and TLS-Only Transition

After having operated our own CA for many years, we recently upgraded our infrastructure to be able to secure connections to the IRC through certificates signed by Let's Encrypt. In addition we will finally drop support for plaintext connections.

Therefore after 2018/11/21 connections to hackint IRC servers
- will be presented with a certificate signed by Letsencrypt

And after 2018/11/30 new connections
- will require TLS on port 6697
- will **not be possible** through plaintext on port 6667

Please take the time to update your clients accordingly and remember to connect to either `irc.hackint.org` or `irc.hackint.eu`.

We will additionally drop support for the channel mode `+S` and extban `$z`, which allows more flexible termination of other connection types without prejudice.

#### Onion Services
Onion services will be stripped of their TLS layer and port and offer instead connections secured by Tor on port 6667. They will not be marked as using TLS but the security should be equivalent.

#### DN42 (after 2018/11/06)
DN42 connectivity will be TLS-only as well, featuring a certificate signed by the DN42 Certificate Authority. We implemented SNI support into charybdis, the ircd we use and are planning to upstream those changes.

### 2018/10/28 Matrix Bridging Sunset

We are deprecating access to hackint from within Matrix and will initiate the bridges shutdown after 2018/12/31. From that point on matrix rooms hosted on irc.hackint.org will become unreachable, IRC identities will be disconnected accordingly.

Providing a Matrix homeserver and bridge is a huge drain on our resources, easily exceeding the requirements for the remainder of our infrastructure. The reasons mostly come down to the following:
- memory intensiveness
- excessive logging to database, even though we're only relaying information
- clients are occasionaly not properly rejoined, but might be able to read messages nevertheless
- user connections are never culled, even when they become unused

Additionally we want to express clearly, that we disallow the bridging of Matrix in general, since some of these issues are universal to its bridging stack and at the same time intolerable.

Migration recommendations include several self-hosted, native and persistent IRC clients
- [Weechat](https://weechat.org/) (ncurses, relaying)
- [Quassel](https://quassel-irc.org/) (relaying)
- [The Lounge](https://thelounge.chat/) (web)

as well as bridged protocols
- XMPP (multiple clients, [media sharing](https://xmpp.org/extensions/xep-0363.html))
  - configure your XMPP-Server to support [Stream Management](https://xmpp.org/extensions/xep-0198.html) and [MAM](https://xmpp.org/extensions/xep-0313.html)

and hosted options, which we will not advertise for.

### Jan 1 2016
After finalising our upgrade of the GroupServ interface, we now would like to announce the availability of custom group-based virtual hosts. Currently, this is an offer for hackerspaces, Freifunk communities, and FOSS projects only - other applications may be evaluated on a case-by-case basis.

If you are a group founder (flag +F), you can join the #hackint channel and request your vhost. Members of the group need the +v flag to have the custom virtual host offered through HostServ.

Happy New Year!

### Aug 18 2015
We're now providing a https-enabled [webchat interface](/webchat)!


### Jul 9 2015
We replaced our [Certificate Authority](/ca) to support contemporary security standards. Please take the time to properly verify the new root certificate before using it.


### Feb 2 2015
Access from i2p is no longer possible. This is due to the resource hungry i2p software, compared to other parts of the IRC ecosystem, as well as due to very low usage, averaging only about five users.
We're sorry for this and hope to remedy the situation in the future; at present, however, due to resource shortage this step has become necessary.

### Jan 31 2015
We have a [new policy](connect#Tor) on anonymous access. Registration for anonymous users has been limited.
