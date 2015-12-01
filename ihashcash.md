## Anonymous access

Anonymous access to hackint has been abused in the past. We do not wish to disable anonymous access, so we are introducing a new policy: Users wishing to connect to hackint anonymously have two possibilities:

1. Connect via a Tor Hidden Service requiring SASL Authentication

   This means that you need an account before you can access hackint anonymously. In order to create an account **anonymously**, please use our [online registration form](http://lechuck.hackint.org/hashcash/).

   Users connecting this way will receive the hostmask **\*@gateway/tor-hashcash-verified**.

2. There exists a second Tor entry node that can be used without SASL.

  Users connecting this way will receive the hostmask **\*@gateway/tor-unverified**.

We hope that this new policy will reduce abuse and prevent legitimate, anonymous users from being banned in channels.


## SASL authentication

[SASL authentication](http://ircv3.net/specs/extensions/sasl-3.1.html) is an extension to the IRC client to server protocol that makes authentication a part of the initial IRC registration handshake. By the time you are able to join channels, you are already identified against NickServ.

The only downside of this is, that any time services are down, you will not be able to connect. This is a situation that occurs only very rarely.
