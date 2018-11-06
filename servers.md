# Servers
| Description                          | Plain                     | TLS (recommended)                                       |
|--------------------------------------|---------------------------|---------------------------------------------------------|
| Round Robin:                         | <s><irc://irc.hackint.org></s>   | <ircs://irc.hackint.org:6697>                    |
| From within [dn42.net] / [chaosvpn]  | <s><irc://irc.hackint.dn42></s>  | <ircs://irc.hackint.dn42:6697>                   |
|                                      | <s><irc://irc.hackint.hack></s>  | <s><ircs://irc.hackint.hack:6697></s>            |
| [Tor] (SASL)                         | n/a                       | <irc://nakufgztylanf4mw.onion:6667>                     |
| [Tor] (SASL) <small>v3</small>       | n/a                       | <irc://dtlbunzs5b7s5sl775quwezleyeplxzicdoh3cnhm7feolxmkfd42nqd.onion:6667> |
| [Tor]                                | n/a                       | <irc://5ogdsfyoqk47ompu.onion:6667>                     |
| [Tor] <small>v3</small >             | n/a                       | <irc://ncwkrwxpq2ikcngxq3dy2xctuheniggtqeibvgofixpzvrwpa77tozqd.onion:6667> |
| Jabber/XMPP                          | n/a                       | *#channel*@irc.hackint.org                              |
| [Matrix] *until 2018/12/31*          |                           | *#channel*:irc.hackint.org                              |

### DN42

The DN42 entrypoint uses a certificate signed by [their own CA](https://dn42.net/services/Certificate-Authority). Using this certificate requires a client that supports Server Name Indication (SNI).

### Tor

*The TLS port for all onion services will be deactivated after 2018/11/21, use the plaintext port instead.*

We offer two Tor hidden services (v2) to connect to hackint with. Both of them require End-to-End Encryption through TLS. [More...](connect#Tor)

For testing purposes two additional Onion services (v3) have been set up, your feedback to us and the Tor project is very welcome.

### Jabber

We are running a jabber to IRC bridge that enables the use of IRC Channels as Jabber MUCs. For a good mobile experience configure your XMPP-Server to support [Stream Management](https://xmpp.org/extensions/xep-0198.html) and [MAM](https://xmpp.org/extensions/xep-0313.html).


Just start a MUC (Groupchat) with *#channel*@irc.hackint.org.

Read up on how to effectively use the bridge with extended features like persistence and message archiving in the [official documentation](https://doc.biboumi.louiz.org/user.html).

### Matrix

*Matrix Bridging is due to be deprecated after 2018/12/31*

We are running a Matrix IRC bridge that enables Matrix users to have a transparent IRC connection and join IRC channels.

Simply join *#channel:irc.hackint.org* from your Matrix client.

[dn42.net]: https://dn42.net
[chaosvpn]: https://wiki.hamburg.ccc.de/ChaosVPN
[Tor]: https://www.torproject.org/
[Matrix]: https://matrix.org
