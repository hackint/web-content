## Connecting

When connecting directly from the internet, not using Tor, please set up your client to use the round-robin DNS. We encourage you to use TLS on ports 6697 and 9999 whenever possible.

For connecting through Tor we provide hidden services, one that requires SASL authentication (and therefore an active nickserv account) and one that does not. To acquire a nickserv account anonymously you may choose to use the [Hashcash registration form](http://hackint.org/ihashcash.html).

### Certificate Authority

All hackint servers are using 4096bit RSA Keys, with SHA256 signatures. Both CRL and OCSP are available.

For further details see the page regarding our [certificate authority](/ca).

### Establishing a secure connection

To verify the authenticity of the server you connect to, download and verify [Hackint IRC Network Root CA](/ca/rootca.crt) and connect to the hackint irc network using a command like this:

#### irssi

<pre>/server -ssl -ssl_verify -ssl_cafile /PATH/TO/hackint-rootca.crt irc.hackint.org 9999</pre>

#### weechat
(mind issue [#438](https://github.com/weechat/weechat/issues/438) )
<pre>
/server add hackint irc.hackint.org/6697 -ssl -autoconnect
/set weechat.network.gnutls_ca_file /PATH/TO/hackint-roootca.crt
</pre>
