## Anonymous access

Anonymous access to hackint has been abused in the past. We do not wish to disable anonymous access, so we are introducing a new policy: Users wishing to connect to hackint anonymously have two possibilities: You can connect to Tor via entry point a with mandatory SASL. This means that you need an account before you can access hackint anonymously. You will get an individual vhost when connecting. In order to create an account **anonymously**, please [use our online registration form](http://lechuck.hackint.org/hashcash/). **There exists a second Tor entry node that can be used without SASL.** Users connecting that way will be identified with the hostname gateway/tor-unverified. We hope that this new policy will reduce abuse and prevent legitimate anonymous users from being banned in all channels.
Comments about this new policy are welcome in #hackint.


## SASL authentication

SASL authentication is an extension to the IRC client to server protocol that makes authentication part of the initial IRC registration handshake. Meaning, by the time you have a nick in the irc network and are able to join channels, you are registered with services. The downside of this is that any time services are down, you will not be able to connect to the IRC network.
