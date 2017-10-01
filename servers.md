## Servers
| Description                          | Plain                     | TLS (recommended)                                       |
|--------------------------------------|---------------------------|---------------------------------------------------------|
| Round Robin:                         | <irc://irc.hackint.org>   | <ircs://irc.hackint.org:9999>                           |
| From within [dn42.net] / [chaosvpn]  | <irc://irc.hackint.dn42>  | <ircs://irc.hackint.dn42:9999>                          |
|                                      | <irc://irc.hackint.hack>  | <ircs://irc.hackint.hack:9999>                          |
| [Tor] (SASL)                         | n/a                       | <ircs://nakufgztylanf4mw.onion:6697>                    |
| [Tor]                                | n/a                       | <ircs://5ogdsfyoqk47ompu.onion:6697>                    |
| [Tor] (SASL, Onion Service v3)       | n/a                       | <ircs://dtlbunzs5b7s5sl775quwezleyeplxzicdoh3cnhm7feolxmkfd42nqd.onion:6697> |
| [Tor] (Onion Service v3)             | n/a                       | <ircs://ncwkrwxpq2ikcngxq3dy2xctuheniggtqeibvgofixpzvrwpa77tozqd.onion:6697> |
| Jabber/XMPP                          | n/a                       | *#channel*@irc.hackint.org                              |
| [Matrix]                             |                           | *#channel*:irc.hackint.org

### Tor

We offer two Tor hidden services to connect to hackint with. Both of them require End-to-End Encryption throuh TLS. [More...](connect#Tor)

### Jabber

We are running a jabber to IRC bridge that enables the use of IRC Channels as Jabber MUCs.

Just start a MUC (Groupchat) with *#channel*@irc.hackint.org.

### Matrix

We are running a Matrix IRC bridge that enables Matrix users to have a transparent IRC connection and join IRC channels.

Simply join *#channel:irc.hackint.org* from your Matrix client.

*Note: IRC connections through Matrix are currently not flagged as encrypted and therefore cannot join channels that have channel mode +S (SSL/TLS required) set.*


[dn42.net]: https://dn42.net
[chaosvpn]: https://wiki.hamburg.ccc.de/ChaosVPN
[Tor]: https://www.torproject.org/
[Matrix]: https://matrix.org
