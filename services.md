## Services

We offer both the usual services like **ChanServ**, **NickServ** and **GroupServ**, along with some custom services. Official services can be recognized by their hostmask: `services.hackint.org`.

To get help with a service, message it with the **help** command. For example with NickServ that is:

```
/msg NickServ help
```

### NickServ
This service will protect your nickname. Certain access rights to *channels* or *groups* might be linked to it.

The most important commands are:
- Register a nickname
  ```
  /msg NickServ register <password> <email>
  ```
- Authenticating
  ```
  /msg NickServ identify <password>
  ```
  *While authenticating by password is fundamentally possible, we recommend to
either use CertFP or SASL.*

### ChanServ
Enables registration of channels to secure ownership and enable management of access flags for both *users* and *groups*.

*Using this service requires a registered account with NickServ.*

The most important commands are:
- Register a channel
  ```
  /msg ChanServ register <#channel>
  ```
- Manage Permissions
  ```
  /msg ChanServ flags <#channel> <nickname> <+-flags>
  ```

### GroupServ
Provides an abstraction layer for group-based access management. Registered
NickServ accounts may create and invite other registered users into groups.
Group names are prefixed by an exclamation mark, like `!groupname`.

*Using this service requires a registered account with NickServ.*

The most important commands are:
- Create a group
  ```
  /msg GroupServ register <!group>
  ```
- Invite someone to a group
  ```
  /msg GroupServ invite <!group> <nickname>
  ```
- Join a group (either by invite or if its open)
  ```
  /msg GroupServ join <!group>
  ```
- Manage group access
  ```
  /msg GroupServ flags <!group> <nickname> <+-flags>
  ```

### HostServ
Provides users with custom with virtual hostnames. The available selection of
hosts usually consists of `hackint/user/$account` and the ones gained through
group memberships.

*Using this service requires a registered account with NickServ.*

The most important commmands are:
- View available vHosts
  ```
  /msg HostServ offerlist
  ```
- Select vHost
  ```
  /msg HostServ take <host>
  ```

### ALIS
Lists available channels with lots of filter options available.

The most important commmands are
- Find matching channels:
  ```
  /msg ALIS list <pattern>
  ```
  *You should really check out all the available patterns!*

### LogServ (*unavailable at present*)

Provides a few lines of backlog to joining users, which is similar to how Jabber MUCs work.

### Greasel
The Greasel fights spam and currently does not offer any user interface. This might change in the future.
