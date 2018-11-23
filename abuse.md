# Abuse Handling

HackiNT is a communications network. We do not accept any malicious behavior as it negatively affects the user experience. This includes, but is not limited to, spamming, flooding, or creating public channel logs without the channel owners permission.

If you or your channel is affected by any abusive behavior, you may consider the following actions to protect yourself. You may also report such behavior in `#hackint`. Please refrain from retaliating using abusive behaviour.


## Query

Botnets will sometimes try and directly query people. Automatic abuse handling in this scenario is difficult as we will under no circumstance monitor private communications.

Your best bet is to restrict which users may contact you in a query, by setting one of the following user modes:

| User Mode | Who can query you? |
| --------- | ----------- |
| +R        | <ul><li>Users identified with NickServ</li><li>Users that you have allowed via `/accept`</li></ul> |
| +g        | <ul><li>Users that you have allowed via `/accept`</li></ul> |

If your client support `/umode`, else `/mode`:
```
/umode +R
/mode <nick> +R
```


## Channel

Proper handling of channel abuse requires knowledge of the available [channel modes](/cmodes) and [extbans](/extban). The modes which are a good fit depends on your channels user base, requirements for openness and pain tolerance.

If your channel experiences abuse and there are no operators on the channel, please ask for help in `#hackint`.

When a channel is first created the default modes are `+nt`, thereby
  - preventing users who are not on the channel from sending messages to the channel
  - preventing non-operators to change the topic

We recommend registering your channel with ChanServ and maintaining access for operators through ChanServ flags.

### Restrict who can join your channel

#### Secret

If people don't know your channel exists abuse is very unlikely to happen. Set channel mode **`+s`** to hide your channel in `/list` and prevent it from being shown in the `/whois` of users who are joined in the channel.

**Example:**
```
/mode #channel +s
```

#### Registered Only / Invite only

Registering with NickServ, while preventing others from using your nickname and tying ACLs to you, can also be used as a criteria to allow users to join a channel. As account registration can be properly rate-limited it limits automated abuse. Two possiblities:

**a)** Set **`+r`** to require users to be identified with any NickServ account at all before joining
```
/mode #channel +r
```
  
**b)** Set **`+i`** to require users to be invited to the channel and maintain an invite list granting access based on NickServ account: **`+I $a:someaccount`**.
  
**Example:**
```
/mode #channel +i
/whois foobar
[...]
[foobar] is logged in as barbaz
[..]
/mode #channel +I $a:barbaz
```

#### Ban
 
If you notice a pattern in the abusers nickname, ident, gecos or hostname you can use **`+b <mask>`** to ban the users. Note that abusers might be persistent and can adapt to your banmask.

**Example:**
```
villain (~villain@ec2-35-180-86-176.eu-west-3.compute.amazonaws.com) has joined #channel
/mode #channel +b *!*@*.compute.amazonaws.com
/kick villain
```
  

### Restrict who can write what to your channel

#### Moderated

When your channel has a very static userbase equipping legitimate users with Voice ``+v`` and setting **`+m`**, the moderated flag, prevents users without voice from talking.

**Example:**
```
/mode #channel +vvv user1 user2 user3
/mode #channel +m
```

#### Operator-Moderated

When a message cannot be sent to channel due to one of `+m`, `+b` or `+q` it is instead sent to operators. A common way to employ this is by setting this in combination with either `+q $~a` (quiet unregistered users), or `+q $~z` (quiet non-tls users) 
    
**Example:**
```
/mode #channel +zq $~a
```

#### Quiet

If you notice a pattern in the abusers nickname, ident, gecos or hostname you can use **`+q <mask>`** to quiet the users. Note that abusers might be persistent and can adapt to your quietmask.

**Example:**
```
villain (~villain@ec2-35-180-86-176.eu-west-3.compute.amazonaws.com) has joined #channel
/mode #channel +q *!*@*.compute.amazonaws.com
```

#### Color/Bold/Underline

Abusive people usually want to draw attention to their messages and might use techniques like color, notices or CTCP messages. There are channel modes that prevent them from being sent at scale to a channel.

| Channel Mode | Result |
| --- | --- |
| +c | All markup (color, bold, underline, etc.) is stripped |
| +C | Prevent CTCP messages from being sent to channel |
| <s>+T</s> | <s>Prevent notices from being sent to channel</s> | 

**Example:**
```
/mode #channel +cC
```


## More elaborate abuse handling schemes

### Sigyn

We provide a hosted bot that employs pattern matching and a coarse detection of the usual spam detection measures and will respond to abuse on a network-wide level.
During persistent channel abuse Sigyn might reduce communications for unregistered users.

If your channel is somewhat large you can have an Operator assign it to your channel by asking in `#hackint`.

#### Unkline

For klines that resulted from abuse in a channel where you have operator status, Sigyn allows you to have their ban autmatically lifted:

Example:
```
/msg Sigyn unkline niceperson
```


### Limnoria: Chantracker

[Chantracker](https://github.com/ncoevoet/ChanTracker) is a powerful abuse handling plugin for [Limnoria](https://github.com/ProgVal/Limnoria) that can be assigned to your own channel, but requires self-hosting.

The feature list reads as follows:
- flood detection
- low-rate flood detection: flooding but with client rate-limiting
- repeat detection
- massRepeat detection: when same message comes from different users
- capslock: detect people who are EXTREMELY ANGRY
- ctcp: detect sending CTCP to the channel
- notices: detect sending notices to the channel
- hilight: nick spam
- nick: nick change spam
- cycle: join/part flood
- massJoin
- evades of quiet/bans via gateway/ ( if resolveIp is True )
- clones detection





