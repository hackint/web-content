# Transport / Matrix

| Portal rooms              | Host-Cloak       |
|---------------------------|------------------|
| #yourchannel:hackint.org  | gateway/matrix/* |

We are currently in a closed testing phase, and a very limited subset of channels was bridged. If you want to participate testing you can join `#hackint-matrix:hackint.org`.

## Retention

Hackint implements a rigorous retention policy, so that we do not store conversations older than two minutes. As such we do not participate in providing backlog to remote users, unless they were present at the time, when an event first occured. Other homeservers will likely fill the gap, should your channel have a more relaxed setting concerning history.

Media content shared from the Matrix side will be served up to 90 days via our homeserver.

## Known issues

- Conversations with the Appservice and NickServ happen in plain text, which means sending your password over the bridge will store it on your homeserver, where different retention policies may apply.

