A block cipher is an encryption algorithm that takes a fixed-size input (e.g., b bits) and produces a ciphertext of b bits. If the input is larger than b bits, it can be divided further. 

Different Modes
- *ECB mode: Electronic Code Book mode*
- *CBC mode: Cipher Block Chaining mode*
- *CFB mode: Cipher FeedBack mode*
- *OFB mode: Output FeedBack mode*
- *CTR mode: Counter mode*
- *GCM (Galois/Counter Mode)*
- CCM (Counter with CBC-MAC)
- XTS (XEX Tweakable Block Cipher with Ciphertext Stealing)
- EAX Mode
- OCB (Offset Codebook Mode)
- PCBC (Propagating Cipher Block Chaining)
- LRW (Liskov, Rivest, Wagner) Mode

## IV (initialisation vector)
It is a random or unique value used in combination with a secret key to initialize the encryption process. It ensures that the same plaintext encrypted multiple times will produce different cipher-texts, enhancing security by preventing patterns from emerging.
- Initialization Vector (IV) is a non-secret, unique value.
- Ensure that encrypting the same plaintext with the same key results in different ciphertexts.
### ECB mode
Direct encryption of each block of input plaintext and output is in the form of blocks of encrypted ciphertext.

![[ECB_GFG.png]]

**Advantages:** Faster encryption
**Disadvantage:** Identical plaintext blocks produce identical ciphertext blocks, which can reveal patterns.

*Given a set of ECB encrypted ciphertext's to find one such where one message is repeated*
```
for i in ct:

	nb = len(i) // 16 #16byte block
	bl = [i[j*16:(j+1)*16] for j in range(nb)]
	if len(set(bl)) == nb:
		continue
	else:
		ans.append(bl)
```

Here:
1. Find the number of byte blocks in the ciphertext
2. Divide the ciphertext into 16byte blocks and store in a list
3. Find the length of the `set(byte_block_list)`:
	If the ciphertext's in this doesn't repeat then there will be no change in the set. But if ciphertext does repeat then only one copy of that will exit (thus changing the number of byte blocks in the list)
4. Check where the length of the `set()` isnt equal to the original number of byte blocks.


### CBC mode
In CBC, the previous cipher block is given as input to the next encryption algorithm after XOR with the original plaintext block.

![[CBC_GFG.png]]

**Common exploits:** Padding Oracle Attack, Bit Flipping Attacks, Predictable IV's

##### Padding Oracle Attack

##### Bit Flipping Attack

##### Predictable IV's

### CFB mode
Here the block-cipher is converted into a stream cipher. Its stream cipher cuz, since no padding - it will be faster, it can be encrypted, sent and decrypted in real time as we need not wait and the length of plaintext = length of ciphertext.   
![[CFB_GFG.png]]

### OFB mode
If the keystream is reused, security is compromised.

![[OFB_GFG.png]]

### CTR mode
Size of the counter will be the size of the plane-text. 

![[CTR_GFG.png]]

### GCM mode
H is basically 128 null bits (0's) encrypted using AES with the key 
![[GCM_GFG.png]]

