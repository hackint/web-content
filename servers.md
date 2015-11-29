## Servers
| Description                          | Plain                     | TLS (recommended)                                       |
|--------------------------------------|---------------------------|---------------------------------------------------------|
| Round Robin:                         | <irc://irc.hackint.org>   | <ircs://irc.hackint.org:9999>                            |
| From within [dn42.net] / [chaosvpn]  | <irc://irc.hackint.dn42>  | <ircs://irc.hackint.dn42:9999>                           |
|                                      | <irc://irc.hackint.hack>  | <ircs://irc.hackint.hack:9999>                           |
| [Tor] (SASL)                         | n/a                       | <ircs://nakufgztylanf4mw.onion:6697>                     |
| [Tor]                                | n/a                       | <ircs://5ogdsfyoqk47ompu.onion:6697>                     |
| Jabber/XMPP                          | n/a                       | *#channel*@irc.hackint.org                              |

### Tor

We offer two Tor hidden services to connect to hackint with. Both of them require End-to-End Encryption throuh TLS.

If you need to authenticate with NickServ you are required to connect with SASL. If you don't have a NickServ account yet you
might want to create one anonymously through the [Hashcash](/ihashcash) registration method, as NickServ access is disabled when connecting
through Tor hidden services due to abuse.

### Jabber

We are running a jabber to IRC bridge that enables the use of IRC Channels as Jabber MUCs.

Just start a MUC (Groupchat) with *#channel*@irc.hackint.org.


[dn42.net]: https://dn42.net
[chaosvpn]: https://wiki.hamburg.ccc.de/ChaosVPN
[Tor]: https://www.torproject.org/
