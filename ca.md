# Certificate Authority

All server certificates on port `6697/tcp` are exclusively signed by the [Hackint IRC Network Intermediate CA G1]. The „Hackint IRC Network Intermediate CA G1“ in turn is signed by the [Hackint IRC Network Root CA], which is the only CA you should trust when connecting to the hackint irc network.

A common certificate chain will look like this, where `0` is the IRC Server, signed by the
intermediate CA, and `1` is the intermediate CA signed by the Root CA.

```
Certificate chain
 0 s:/C=US/O=Hackint IRC Network/CN=morgan.hackint.org
   i:/O=Hackint IRC Network/OU=http://www.hackint.org/CN=Hackint IRC Network Intermediate CA G1/emailAddress=ca@hackint.org
 1 s:/O=Hackint IRC Network/OU=http://www.hackint.org/CN=Hackint IRC Network Intermediate CA G1/emailAddress=ca@hackint.org
   i:/O=Hackint IRC Network/OU=http://www.hackint.org/CN=Hackint IRC Network Root CA/emailAddress=ca@hackint.org
```

### Features

#### Implemented:
- all certificates are using at least 4096bit RSA keys
- all certificates are signed using at least SHA256 message digest
- all server certificates support both [CRL](https://en.wikipedia.org/wiki/Revocation_list) and [OCSP](https://en.wikipedia.org/wiki/Online_Certificate_Status_Protocol)

#### Todo
- OCSP Stapling and Client Support for it

### Bootstrapping trust

Before importing our CA you should verify your trust in it. Only then you can properly verify a servers identity and therefore ensure you will not be victim to a [MITM](https://en.wikipedia.org/wiki/Man-in-the-middle_attack)-Attack.

There are, as always, several grades of verification and you should decide, depending on
your attacker model, which you want and/or need. Unfortunately, bootstrapping trust can be quite tricky.   

#### The naive approach (Fingerprint)
Verify the serial SHA256 fingerprint given on this website against the certificate you downloaded.

If however someone is able to compromise or imitate this website, they will also be able to change the fingerprint presented here.

[Hackint IRC Network Root CA] (Right click & save to disk)

**SHA256** `06:E3:9C:65:50:76:53:10:DE:54:8A:DE:11:71:12:A4:6E:83:2F:9C:EE:B8:FD:63:E0:BD:DC:83:34:BC:75:F8`

**SHA512**
`23:DA:4A:14:18:80:E1:4B:31:EB:CC:B5:BD:C2:C0:15:C6:2D:00:31:79:A6:38:C1:B2:6B:17:20:C0:50:8B:D7:ED:FE:6E:7F:94:26:87:94:C4:40:37:51:61:D7:F7:EF:7D:E7:97:86:70:3A:86:C6:F1:25:4A:ED:2A:DA:28:97`

To calculate the fingerprint of the certificate you downloaded, use:

```
openssl x509 -noout -fingerprint -sha256 -in rootca.crt
```
If it matches you should now import the certificate into the certificate truststore used by your IRC client.   


#### A better approach (GPG)
The [Hackint IRC Network Root CA] certificate has been GPG signed by most of the irc server administrators. Hopefully, you know one of the admins or know someone who signed one of the admin's pgp keys.

You can get a [combined signature file] for checking all signatures at once, or use individual signatures:
- [andi-.asc],
- [bspar.asc],
- [cr0n.asc],
- [hansenerd.asc],
- [hexa-.asc],
- [maniactwister.asc],
- [major.asc],
- [rdnzl.asc],
- [undermink.asc],
- [zakx.asc]

To verify the authenticity of the [Hackint IRC Network Root CA], download one or more signature file(s) and then use:

`gpg --verify combined.asc rootca.crt`

Depending on your GPG Truststore this might or might not get any usable results. If one or more signatures match, you should now import the certificate into your IRC clients certificate truststore.

[Hackint IRC Network Root CA]: /crt/rootca.crt
[Hackint IRC Network Intermediate CA G1]: /crt/intermediate1.crt
[combined signature file]: /crt/sigs/combined.asc
[andi-.asc]: /crt/sigs/andi-.asc
[bspar.asc]: /crt/sigs/bspar.asc
[cr0n.asc]: /crt/sigs/cr0n.asc
[hansenerd.asc]: /crt/sigs/hansenerd.asc
[hexa-.asc]: /crt/sigs/hexa-.asc
[maniactwister.asc]: /crt/sigs/maniactwister.asc
[major.asc]: /crt/sigs/major.asc
[rdnzl.asc]: /crt/sigs/rdnzl.asc
[undermink.asc]: /crt/sigs/undermink.asc
[zakx.asc]: /crt/sigs/zakx.asc
