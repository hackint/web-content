## Extended Bans (extban)

Changing channel modes is an operation restricted to channel operators, who can be recognized by the @-prefixed to their name. They mostly regulate access and moderation.
Extended bans provide additional possibilities to control entries in channel access lists (ban, quiet, exempt, invite). They can offer fine-grained access control and are often used in spam reduction measures.

Available extbans can be queried via:
```
/quote HELP extban
```
```
MODE <channel> <+|-><b|q|e|I> $[~]<type>[:<data>]

Extended bans (ban conditionals) allow different checks than the usual
nick!user@host or nick!user@ip match to determine whether someone should
be banned, quieted, exempted or invited.

Extended bans are of the form $[~]<type>[:<data>]. The <type> is one
character (case insensitive) and determines the type of match. Most types
allow or require an extra field <data>. If the tilde (~) is present, the
result of the comparison will be negated, unless the ban is invalid in which
case it will never match. Invalid bans are ones where <data> is missing but
required or where <data> is otherwise invalid as noted below.

Unless noted below, all types can be used with +b, +q, +e and +I.

 extb Type  - DESCRIPTION
------------------------------------------------------------------------
     $a     - Matches all logged in users
  $a:<mask> - Matches users logged in with a username matching the mask
              (* and ? wildcards)
  $c:<chan> - Matches users who are on the given channel; this is only
              valid if the channel exists and is not +s or +p. (The ops
              of the channel the ban is on cannot necessarily see whether
              the user is in the target channel, so it should not
              influence whether they can join either.)
     $o     - Matches opers (most useful with +I)
  $r:<mask> - Matches users with a realname (gecos) matching the mask
              (* and ? wildcards); this can only be used with +b and +q
  $s:<mask> - matches users connected to a server matching the mask
              (* and ? wildcards); this can only be used with +b and +q
  $j:<chan> - matches users who are or are not banned from a specified
              channel
  $x:<mask> - Bans all users with matching nick!user@host#gecos
     $z     - Matches all SSL users

```
