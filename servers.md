# Servers

| Region        | Address                           |
|---------------|----------------------------------|
| Global        | <ircs://irc.hackint.org:6697>    |
| Europe        | <ircs://irc.eu.hackint.org:6697> |
| - Germany     | <ircs://irc.de.hackint.org:6697> |
| - Netherlands | <ircs://irc.nl.hackint.org:6697> |

We would like to encourage you to authenticate via one of the following schemes:

- password based (*easy*)
  - SASL PLAIN
- certificate based  (*moderately difficult*)
  - SASL ECDSA-NIST256P
  - SASL EXTERNAL
  - CertFP

We're currently using SHA256 fingerprints for SASL External and CertFP.

Enrolling your fingerprint is just a matter of calling:

```
/msg NickServ cert add
```

This will automatically configure the fingerprint of the client 
certificate you are currently connected with. You will now 
automatically be identified by NickServ on every connect, when
you present your client certificate.

Other ways to connect exist, they use transports, check the menu for that.
