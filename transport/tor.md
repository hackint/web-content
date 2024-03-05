# Transport / Tor

| Onion Version | Requirements | Host-Cloak           | Hostname                                                       | Port       |
|---------------|--------------|----------------------|----------------------------------------------------------------|------------|
| v3            | SASL         | gateway/tor-sasl     | dtlbunzs5b7s5sl775quwezleyeplxzicdoh3cnhm7feolxmkfd42nqd.onion | 6667, 6697 |
| v3            | *none*       | gateway/tor-anon     | ncwkrwxpq2ikcngxq3dy2xctuheniggtqeibvgofixpzvrwpa77tozqd.onion | 6667       |

We do allow anonymous access to hackint using Tor's Onion v3 services. SASL authentication is not required, but you will receive another host cloak, that has a better reputation, as it requires you to be in possession of a services account. Identifying to an existing account from tor-anon gateway is not possible.

Do note that TLS (6697) is required for SASL *external* authentication to work on IRC. Regular SASL will still work without TLS.

### TLS on Onion Services

To connect using TLS through Tor, you can add the following configuration to your `torrc`:
```
# hackint.org irc onion service
MapAddress guybrush.hackint.org dtlbunzs5b7s5sl775quwezleyeplxzicdoh3cnhm7feolxmkfd42nqd.onion
```
Then, connect using `guybrush.hackint.org/6697` (after configuring the proxy)

For most users the end-to-end encryption provided by Onion services will be sufficient. For everyone else we provide TLS on port 6697, to enable true end-to-end encryption in a few cases. It also enables CertFP and SASL external over Tor.

Otherwise, one of the cases where this might make sense is in setups like Qubes OS or Whonix, where the Tor traffic may be terminated inside another trust domain, and which would then be forwarded plainly to your client.

### Quick setup guide

This guide assumes that you have Tor installed locally with the SocksPort exposed at *127.0.0.1:9050* (should be the default)

#### [WeeChat](https://weechat.org)

Configure Tor as a socks5 proxy and pick a host from above.
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

### Anonymous Account Registration

We also allow the anonymous creation of services accounts through a [proof of work system](https://en.wikipedia.org/wiki/Proof-of-work_system), where your computer has to solve a mathematical problem, thereby offering a trade-off between abuse and the justified wish for anonymity.

**[Register account via Hashcash](https://hashcash.hackint.org)**
