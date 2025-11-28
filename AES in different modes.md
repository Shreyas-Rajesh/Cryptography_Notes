

The size of an AES block is 128 bits, whereas the size of the encryption key can be 128, 192 or 256 bits.

Different Modes
- ECB mode: Electronic Code Book mode
- CBC mode: Cipher Block Chaining mode
- CFB mode: Cipher FeedBack mode
- OFB mode: Output FeedBack mode
- CTR mode: Counter mode

The attack mode:
- PA: Padding attack
- CPA: Chosen Plaintext Attack
- CCA: Chosen Ci

### EBC mode
![[AES_EBC.png]]

the ECB mode needs to pad data until it is same as the length of the block. Then every block will be encrypted with the same key and same algorithm. So if we encrypt the same plaintext, we will get the same ciphertext. So there is a high risk in this mode. And the plaintext and ciphertext blocks are a one-to-one correspondence. Because the encryption/ decryption is independent, so we can encrypt/decrypt the data in parallel. And if a block of plaintext or ciphertext is broken, it won’t affect other blocks.

## CBC
uses IV and XOR


`from Crypto.Cipher import AES`
cipher = AES.new(key, AES.MODE)

`Crypto.Util.Padding` - to padding
`Crypto.Util.number.getPrime()`

`Crypto.Util.number.bytes_to_long(s)`
`Crypto.Util.number.long_to_bytes(s)`
int.to_bytes