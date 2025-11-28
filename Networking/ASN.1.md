ASN.1 (Abstract Syntax Notation One) is a _standard way_ to describe data structures so they can be encoded and decoded consistently across different systems, programming languages, and hardware.

- **Define exact structure:**  
    What fields exist, their types, and the allowed formats.
- **Define exact binary encoding:**  
    So any two implementations can serialize/parse the same bytes without ambiguity.

Different types of encoding:
- **DER (Distinguished Encoding Rules)** — used in X.509 certificates
- **BER (Basic Encoding Rules)**
- **CER (Canonical Encoding Rules)**

***PEM files are basically ASN.1 structured data encoded in DER (Converted to bytes) form represented in base64***

How to access PEM files:
`from Crypto.PublicKey import RSA` 
`RSA.importkey(open("location of pem","rb").read())`
This creates and object. 
1. To see all the attributes of a object - `dir(object)`
2. To access the attribute value - `object.attribute`

