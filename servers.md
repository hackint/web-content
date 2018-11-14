### Round-Robin record sets
| Region        | Adress                           |
|---------------|----------------------------------|
| Global        | <ircs://irc.hackint.org:6697>    |
| Europe        | <ircs://irc.eu.hackint.org:6697> |
| - Germany     | <ircs://irc.de.hackint.org:6697> |
| - Netherlands | <ircs://irc.nl.hackint.org:6697> |

We would like to encourage you to authenticate via SASL methods PLAIN (*easy*) or EXTERNAL (*moderately difficult*).

### Jabber/XMPP

| Address                    |
|----------------------------|
| *#channel*@irc.hackint.org |

We are running a Jabber to IRC bridge that enables the use of IRC Channels as Jabber MUCs. For a good mobile experience configure your XMPP-Server to support [Stream Management](https://xmpp.org/extensions/xep-0198.html) and [Message Archiving](https://xmpp.org/extensions/xep-0313.html).

Just join our MUCs (Groupchat) with the name *#channel*@irc.hackint.org.

Read up on how to effectively use the bridge with extended features like persistence and message archiving in the [official documentation](https://doc.biboumi.louiz.org/user.html).

### From DN42
| Requirements                          | Addresss                       |
|---------------------------------------|--------------------------------|
| [dn42.net] Participation | <ircs://irc.hackint.dn42:6697> |

The DN42 entrypoint uses a certificate signed by [their own CA](https://dn42.net/services/Certificate-Authority). Using this certificate requires a client that supports Server Name Indication (SNI).

Connection should also be possible from within [chaosvpn] and Freifunks [Intercity-VPN], provided you don't filter DN42 address space.

### From Tor

| Onion Version | Requirements | Address                                                                     |
|---------------|--------------|-----------------------------------------------------------------------------|
| v3            | SASL         | <irc://dtlbunzs5b7s5sl775quwezleyeplxzicdoh3cnhm7feolxmkfd42nqd.onion:6667> |
| v2            | SASL         | <irc://nakufgztylanf4mw.onion:6667>                                         |
| v3            | *none*       | <irc://ncwkrwxpq2ikcngxq3dy2xctuheniggtqeibvgofixpzvrwpa77tozqd.onion:6667> |
| v2            | *none*       | <irc://5ogdsfyoqk47ompu.onion:6667>                                         |


**The TLS port for all onion services will be deactivated after 2018/11/21, use the plaintext port instead.**

We provide access via the [Tor] networks [Onion services]. As Tor already provides an encrypted transport and getting a certificate for a .onion domain is stupidly expensive we only provide plaintext connections on port 6667. This should not harm the confidentiality of your connection.

[More...](connect#Tor)


### From Matrix

| Addresss                   |
|----------------------------|
| *#channel*:irc.hackint.org |

**Matrix Bridging is due to be deprecated after 2018/12/31**

We are running a Matrix IRC bridge that enables Matrix users to have a transparent IRC connection and join IRC channels.

Simply join *#channel:irc.hackint.org* from your Matrix client.

[dn42.net]: https://dn42.net
[chaosvpn]: https://wiki.hamburg.ccc.de/ChaosVPN
[Intercity-VPN]: https://wiki.freifunk.net/IC-VPN
[Tor]: https://www.torproject.org/
[Onion services]: https://www.torproject.org/docs/onion-services.html.en
[Matrix]: https://matrix.org
