A digital certificate is a file or electronic password that proves the authenticity of a device, server, or user through the use of cryptography and the `public key infrastructure (PKI)`. Another common use of digital certificates is to confirm the authenticity of a website to a web browser, which is also known as a secure sockets layer or `SSL certificate`.

Digital Certificates contains identifiable information such as: 
1. device’s Internet Protocol (IP) address or serial number.
2. copy of a public key from the certificate holder, which needs to be matched to a corresponding private key to verify it is real.

*When connecting to a server*:

 Digital certificate (like an X.509 TLS certificate) contains the server’s public key. 
 - The server administrator generates a public/private key pair.
 - The server sends the public key plus identifying info (domain name, etc.) to a Certificate Authority (CA) as a Certificate Signing Request (CSR).
 - The CA signs it and returns a certificate.
 - The certificate is installed on the server.

When a client connects:
-  The server sends its certificate (containing its public key).
- The client checks: If the certificate is valid, is it signed by a trusted CA, do domain names match
- The client uses the server’s public key to start the secure handshake (e.g., verify signatures or exchange keys).

# Certificate Chain 
A certificate chain is an ordered list of certificates, containing an SSL/TLS Certificate and Certificate Authority (CA) Certificates, that enables the receiver to verify that the sender and all CA's are trustworthy. 
The chain or path begins with the SSL/TLS certificate, and each certificate in the chain is signed by the entity identified by the next certificate in the chain.
A Certificate Authority (CA) is an entity that issues digital certificates and vouches for the identity of the certificate holder. It does this by using its own private keys to sign certificates. The CA operates the infrastructure that creates the certificates used in a certificate chain.

#### Intermediate certificates
- Any certificate that sits between the SSL/TLS Certificate and the Root Certificate is called a chain or Intermediate Certificate. 
- The Intermediate Certificate is the signer/issuer of the SSL/TLS Certificate. 
- The Root CA Certificate is the signer/issuer of the Intermediate Certificate. 
- If the Intermediate Certificate is not installed on the server (where the SSL/TLS certificate is installed) it may prevent some browsers, mobile devices, applications, etc. from trusting the SSL/TLS certificate. 
- In order to make the SSL/TLS certificate compatible with all clients, it is necessary that the Intermediate Certificate be installed.

#### Root certificates / Trust anchor
The chain terminates with a Root CA Certificate. The Root CA Certificate is always signed by the CA itself. The signatures of all certificates in the chain must be verified up to the Root CA Certificate.

Every CA must publish all certificates that they issue to a log, which anyone can search. There is a CT log maintained (go to crt.sh). Take the DER formats shaX or md5 hash to search

![[Certificates_RootCertificate.png]]

# Trust anchor
A trust anchor is typically the CA’s _root certificate_ that has been explicitly trusted by a device or application. It’s not the CA itself — it’s the certificate that establishes the starting point of trust for the certificate chain.


## Analogy
- **CA**: A passport office that issues passports.
- **Trust Anchor**: The master list of passport offices your country trusts.
---

When you connect to a website over HTTPS, the first TLS message sent by the server is the ServerHello containing the server TLS certificate. Your browser verifies that the TLS certificate is valid, and if not, will terminate the TLS handshake. Verification includes ensuring that:  
  

- the name on the certificate matches the domain
- the certificate has not expired
- the certificate is ultimately signed (via a "chain of trust") by a root key of a Certificate Authority (CA) that's trusted by your browser or operating system

---
