## Connecting

When connecting directly from the internet, please set up your client to use the round-robin DNS. We encourage you to use TLS on port 6697 whenever possible.

For connecting through Tor we provide hidden services, one that requires SASL authentication (and therefore an active nickserv account) and one that does not. To acquire a nickserv account anonymously you may choose to use the [Hashcash registration form](http://hashcash.hackint.org), as direct NickServ access through Tor has been disabled.

### Tor

Anonymous access to IRC has a long history of abuse, even until today. As we do not wish to disable anonymous access entirely, we are instead separating anonymous users in two groups. One, which is ratelimited through account creation, and one that isn't. This introduces a powerful mechanism to then control anonymous access on a channel to channel basis.

1. Tor Onion Service **requiring** SASL Authentication

   <ircs://nakufgztylanf4mw.onion:6697> (onion v2)

   <ircs://dtlbunzs5b7s5sl775quwezleyeplxzicdoh3cnhm7feolxmkfd42nqd.onion:6697> (onion v3, requires tor >= 0.3.2.1)

   To connect to this server you do need an account, which you can create *anonymously* through the [Hashcash registration](https://hashcash.hackint.org), it employs a [proof-of-work system](https://en.wikipedia.org/wiki/Proof-of-work_system).

   Users connecting this way will receive the hostmask **\*@gateway/tor-hashcash-verified**.

2. Tor Onion Service without any requirements

   <ircs://5ogdsfyoqk47ompu.onion:6697> (onion v2)

   <ircs://ncwkrwxpq2ikcngxq3dy2xctuheniggtqeibvgofixpzvrwpa77tozqd.onion:6697> (onion v3, requires tor >= 0.3.2.1)

   Users connecting this way will receive the hostmask **\*@gateway/tor-unverified**.

### Certificate Authority

All hackint servers are using 4096bit RSA Keys, with SHA256 signatures. Both CRL and OCSP are available.

For further details check the information on our [certificate authority](/ca).

### Establishing a secure connection

To verify the authenticity of the server you connect to, download and verify [Hackint IRC Network Root CA](/crt/rootca.crt) and connect to the hackint irc network using a command like this:

#### irssi

<pre>/server add -auto -ssl -ssl_verify -ssl_cafile /PATH/TO/hackint-rootca.crt irc.hackint.org 6697</pre>

#### weechat
(mind issue [#438](https://github.com/weechat/weechat/issues/438) )
<pre>
/server add hackint irc.hackint.org/6697 -ipv6 -ssl -autoconnect
/set weechat.network.gnutls_ca_file /PATH/TO/hackint-roootca.crt
</pre>

## Authentication
### SASL authentication

The recommended way to authenticate against our services is through the [SASL authentication](http://ircv3.net/specs/extensions/sasl-3.1.html). It's an extension to the IRC client to server protocol that makes authentication part of the initial IRC registration handshake. By the time you are able to join channels, you are already identified against NickServ.

We currently support the following SASL mechanisms:
- PLAIN
- EXTERNAL (client certificate)

#### weechat
<pre>
/set irc.server.hackint.sasl_mechanism PLAIN
/set irc.server.hackint.sasl_username NICKSERV_NAME
/set irc.server.hackint.sasl_password NICKSERV_PASSWORD
</pre>
