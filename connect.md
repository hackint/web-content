# Connecting

When connecting directly from the internet, please set up your client to use the round-robin DNS at `irc.hackint.org`. We require you to use TLS on port 6697.

## Certificate Verification

**Please make sure you don't disable SSL/TLS verification. You're putting not only yourself but also others at risk, by silently allowing Man-in-the-middle attacks and leaking potentially private conversations.**

All our IRC servers are using 4096 bit RSA keys, with certificates signed with sha256 signatures from Let's Encypt. In general their root certificates should already be a part of your local trust store. 

For more information you can read up on Let's Encrypts [trust chain](https://letsencrypt.org/certificates/).

## Quick setup guide

We support IPv6 connections, require TLS connections and encourage SASL Authentication (PLAIN and EXTERNAL). The examples below show how to enable SASL PLAIN, which is the easiest among the prefered ways for authenticating.

### [WeeChat](https://weechat.org)
```
/server add hackint irc.hackint.org/6697 -ipv6 -ssl -autoconnect
/set irc.server.hackint.sasl_mechanism PLAIN
/set irc.server.hackint.sasl_username <login>
/set irc.server.hackint.sasl_password <password>
/save
/connect hackint
```

### [irssi](https://irssi.org/)

```
/network add -sasl_username <login> -sasl_password <password> -sasl_mechanism PLAIN hackint
/server add -auto -net hackint -ssl -ssl_verify irc.hackint.org 6697
/save
/connect hackint
```
