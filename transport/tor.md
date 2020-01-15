# Transport / Tor

| Onion Version | Requirements | Host-Cloak       | Hostname                                                         | Port |
|---------------|--------------|------------------|------------------------------------------------------------------|------|
| v3            | SASL         | gateway/tor-sasl | <dtlbunzs5b7s5sl775quwezleyeplxzicdoh3cnhm7feolxmkfd42nqd.onion> | 6667 |
| v2            | SASL         | gateway/tor-sasl | <nakufgztylanf4mw.onion>                                         | 6667 |
| v3            | *none*       | gateway/tor-anon | <ncwkrwxpq2ikcngxq3dy2xctuheniggtqeibvgofixpzvrwpa77tozqd.onion> | 6667 |
| v2            | *none*       | gateway/tor-anon | <5ogdsfyoqk47ompu.onion>                                         | 6667 |

We do allow anonymous access to hackint using Tor's Onion services. SASL authentication is not required, but you will receive another host cloak, that has a better reputation, as it requires you to be in possession of a services account.

Onion services after v0.3.2.1 are capable of using the v3 endpoints, those before need to stick to the v2 endpoints.

We only offer plain connections on port 6667 for Onion services, since Tor already end-to-end encrypts the connection. Also proper certificates for `.onion` domains are required to have Extended Validation and are therefore prohibitively expensive.

### Anonymous Account Registration

We also allow the anonymous creation of services accounts through a [proof of work system](https://en.wikipedia.org/wiki/Proof-of-work_system), where your computer has to solve a mathematical problem, thereby offering a trade-off between abuse and the justified wish for anonymity.

**[Register account via Hashcash](https://hashcash.hackint.org)**

### Quick setup guide

This guide requires that you have Tor installed locally with the SocksPort exposed at *127.0.0.1:9050*.

#### [WeeChat](https://weechat.org)

Configure tor as a socks5 proxy and pick a host from above.
```
/proxy add tor socks5 127.0.0.1 9050
/server add hackint-tor <hostname>/<port>
/set irc.server.hackint-tor.proxy "tor"
```

If the host requires SASL authentication, configure it like this:
```
/set irc.server.hackint-tor.sasl_mechanism PLAIN
/set irc.server.hackint-tor.sasl_username <login>
/set irc.server.hackint-tor.sasl_password <password>
```

Finally save and connect.
```
/save
/connect hackint-tor
```
