# Welcome to hackint!

hackint is a communication network for the [hacker](https://en.wikipedia.org/wiki/Hacker_culture) community, but anyone is welcome to use its services. We are fully [ircv3.1](http://ircv3.net/irc/#ircv31) and partially [ircv3.2](https://ircv3.net/irc/#ircv32) compliant.

## News

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

## News Archive

Older news can be found in the [archive](/archive).
