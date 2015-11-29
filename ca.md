## Hackint IRC Network PKI

We are replacing hackint's current PKI to meet contemporary security requirements. All users are encouraged to connect to the hackint irc network using TLS on port 9999.

As soon as the new PKI is in place, all irc server's client connection certificates on TCP port 9999 will be exclusively signed by [Hackint IRC Network Intermediate CA G1](http://hackint.org/ca/intermediate1.crt). The Hackint IRC Network Intermediate CA G1 itself is signed by the [Hackint IRC Network Root CA], which is the only CA you should trust when connecting to the hackint irc network.

### Features of the new PKI

When the new CA is in place,

- all irc servers will be using 4096bit RSA keys and all server certificates will be signed by the new CA using SHA256 message digest and 4096bit RSA signature keys,
- all certificates will include a Certificate Revocation List (CRL) and Online Certificate Status Protocol (OCSP) URL,
- In the future, hopefully all hackint irc servers will implement OCSP stapling and the verification of the certificate status will be mandatory if your client supports it.

### Bootstrapping trust

Before you can trust the CA (and by this trust the server you are connecting to), you need to verify its authenticity.

**A naive approach:** Unfortunately, bootstrapping trust can be quite tricky.
You can find the SHA256 fingerprint of the root CA here. However, if someone is able to change the certificate on this website, she will also be able to change the fingerprint presented here. Thus, you should verify the authenticity of this fingerprint before you trust it :)

[Hackint IRC Network Root CA]:
<pre>SHA256 Fingerprint=06:E3:9C:65:50:76:53:10:DE:54:8A:DE:11:71:12:A4:6E:83:2F:9C:EE:B8:FD:63:E0:BD:DC:83:34:BC:75:F8</pre>

To calculate the fingerprint of the certificate you downloaded, use this command:

<pre>openssl x509 -noout -fingerprint -sha256 -in rootca.crt</pre>

<br/>
**A better approach:** The Hackint IRC Network Root CA certificate has been GPG signed by most of the irc server administrators. Hopefully, you know one of the admins or know someone who signed one of the admin's pgp keys. You can get a combined signature file for checking all signatures at once [here](/ca/sigs/combined.asc), or use the individual signatures: [bspar.asc], [cr0n.asc], [hansenerd.asc], [hexa-.asc], [maniactwister.asc], [major.asc], [rdnzl.asc], [undermink.asc], [zakx.asc]

To verify the authenticity of the Hack.INT IRC Network Root CA, download the signature file(s) and use a command like this:

<pre>gpg --verify combined.asc rootca.crt</pre>

### Establishing a secure connection to the hackint irc network

To verify the authenticity of the server you connect to, download [Hackint IRC Network Root CA] and connect to the hackint irc network using a command like this:

<pre>/server -ssl -ssl_verify -ssl_cafile /PATH/TO/rootca.crt irc.hackint.org 9999</pre>

### Server List

Please use one of our [DNS round robins](/servers). For TLS, use port 9999. Strange certificates may be presented on other SSL ports.


[Hackint IRC Network Root CA]: /ca/rootca.crt
[bspar.asc]: /ca/sigs/bspar.asc
[cr0n.asc]: /ca/sigs/cr0n.asc
[hansenerd.asc]: /ca/sigs/hansenerd.asc
[hexa-.asc]: /ca/sigs/hexa-.asc
[maniactwister.asc]: /ca/sigs/maniactwister.asc
[major.asc]: /ca/sigs/major.asc
[rdnzl.asc]: /ca/sigs/rdnzl.asc
[undermink.asc]: /ca/sigs/undermink.asc
[zakx.asc]: /ca/sigs/zakx.asc
