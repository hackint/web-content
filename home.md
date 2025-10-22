# Welcome to hackint!

hackint is a communication network for the [hacker](https://en.wikipedia.org/wiki/Hacker_culture) community, but anyone is welcome to use its services. We are fully [ircv3.1](http://ircv3.net/irc/#ircv31) and partially [ircv3.2](https://ircv3.net/irc/#ircv32) compliant.

## News

### 2025/10/23 Friendship with `/msg NickServ identify` ended. Now SASL PLAIN is your new best friend.

We are deprecating in-band authentication with `NickServ` through the `IDENTIFY` command starting today.

From **2026-02-01** the only supported authentication methods will be: SASL PLAIN, SASL EXTERNAL, SASL SCRAM-SHA-256, CertFP.

The rough list of reasons are that it is an outdated, insecure, and user-unfriendly way to transmit your credentials.

- Logging in only happens once you are connected, which can lead to races with room permissions
- Time and time again people have posted their credentials onto public channels
- Credentials tend to get stored in your client logs

Clients have a dedicated place to store your credentails these days

We recommend making this migration early, especially if you run a channel and depend on permissions handed
out by the services.

### 2024/10/30 Webchat replacement

We are replacing _KiwiIRC_, the software that powers our webchat.
Starting now, _The lounge_ will be available at [chat.hackint.org](https://chat.hackint.org).

Check out our [documentation](/webchat).

## News Archive

Older news can be found in the [archive](/archive).
