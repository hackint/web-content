# News Archive

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
