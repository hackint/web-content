# Servers

| Region        | Address                           |
|---------------|----------------------------------|
| Global        | <ircs://irc.hackint.org:6697>    |
| Europe        | <ircs://irc.eu.hackint.org:6697> |
| - Germany     | <ircs://irc.de.hackint.org:6697> |
| - Netherlands | <ircs://irc.nl.hackint.org:6697> |

## Authentication

We would like to encourage you to authenticate via [SASL], so you will
already be authenticated before your client tries to join channels,
which results in a smoother connection setup.

- password based (*easy*)
  - [SASL PLAIN]
- certificate based (*moderately difficult*)
  - SASL ECDSA-NIST256P-CHALLENGE (atheme-specific)
  - [SASL EXTERNAL]
  - CertFP

### Certificate Fingerprint (SASL External, CertFP)

To enroll the fingerprint of the certificate you are currently connected
with call:

```
/msg NickServ cert add
```

Presenting the client certificate on connect will subsequently
authenticate you against services.

We're currently using SHA256 fingerprints for SASL External and CertFP.

### Public Key (ECDSA-NIST256P-CHALLENGE)

If you are planning to use ECDSA-NIST256P, generate `prime256v1` ecparams
and store the public key within the services. During the connection phase
a challenge-based authentication will happen.

#### Generate the ecparams and retrieve the public key

```
$ openssl ecparam -genkey -name prime256v1 -out ecdsa.pem
$ openssl ec -noout -text -conv_form compressed -in ecdsa.pem | grep '^pub:' -A 3 | tail -n 3 | tr -d ' \n:' | xxd -r -p | base64
```

#### Configure the public key in your account

```
/msg NickServ set property pubkey <pubkey>
```

#### Configure ecdsa-nistp256-challenge in your client

##### WeeChat

```
/set irc.server.hackint.sasl_username <account>
/set irc.server.hackint.sasl_key </path/to/ecdsa.pem>
/set irc.server.hackint.sasl_method ecdsa-nistp256-challenge
```

## Transports

Other ways to connect exist, they use transports, check the menu for that.

[SASL]: https://ircv3.net/docs/sasl-mechs
[SASL PLAIN]: https://datatracker.ietf.org/doc/html/rfc4616
[SASL EXTERNAL]: https://datatracker.ietf.org/doc/html/rfc4422#appendix-A
