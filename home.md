# Welcome to hackint!

hackint is a communication network for the [hacker](https://en.wikipedia.org/wiki/Hacker_culture) community, but anyone is welcome to use its services. We are fully [ircv3.1](http://ircv3.net/irc/#ircv31) and partially [ircv3.2](https://ircv3.net/irc/#ircv32) compliant.

## News

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

#### DN42
DN42 connectivity will reduced to TLS-only as well, the sockets will be terminated by a stunnel instance, featuring a certificate signed by the DN42 Certificate Authority. This is necessary because IRC support for SNI isn't quite there yet and usage isn't actually high enough to justify an own ircd.

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

and hosted options, which we will not advertise for.


## News Archive

Older news can be found in the [archive](/archive).
