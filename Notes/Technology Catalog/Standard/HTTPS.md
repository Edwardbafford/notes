HTTPS is a secure version of the [HTTP](#HTTP) protocol. The protocol is reliant on [public-private key encryption](#Public%20Private%20Key%20Encryption).

**TLS CIpher Suite** is a set of algorithms used during the HTTPS connection.

**Certificate Authority** is in entity that signs a certificate stating that the domain linked with a public key is valid.

Make sure to enforce certain secure protocols, cipher suites, and CAs to trust.

## **Protocol**

First the connection is established.

Server then sends it's Public Key and Certificate.

The Certificate states that the public key belongs to a domain for a certain date range.

It is assumed that the Certificate message has been signed by a CA's private key.

The Client then tests a set of Public Keys from trusted CAs to sign the certificate.

If the certificate has been signed by a trusted CA and states that the Public Key given by the server does below to the domain name the Server claims to be then the Client can trust that this has been verified by a CA the Client trusts. Therefore proving to the client that the server is who it claims to be.

Otherwise the client can go to the CA's domain and check their certificate. If their certificate has be signed by a trust CA then the client can trust the original server. This is called going up the certificate chain.

![[cert-chain.png]]

The Client then creates a new symmetric key and sends it to the Server, encrypting it with the public key that only the Server's private key can decrypt.

The two sides now use the symmetric key that only they have access to encrypt and decrypt the messages between them.

From here standard HTTP protocol is followed.