AES is a [[Block Ciphers]]. This is an encryption method that is used to secure data by converting it into an unreadable format without the proper key. 

The size of an AES block is 128 bits (16 bytes), whereas the size of the encryption key can be 128, 192 (24 bytes) or 256 bits (32 bytes).

![[AES_Structure_NESO.png]]

![[AES_Enc_Dec_NESO.png]]

#### State
AES works by creating a 4x4 matrix grid, each matrix is called `state`:
```
[b0  b4  b8  b12]
[b1  b5  b9  b13]
[b2  b6  b10 b14]
[b3  b7  b11 b15]
```

#### Key Expansion:
- a 16-byte key
- expands it into 44 words (each word = 4 bytes) - 176 bytes
- grouped as 11 round keys (Round 0 to Round 10)  
`w[0,3]`, `w[4,7]` etc are all words derived from the key. 

> [!Note] Keys are not reused

#### Encryption:
###### Round 0
This is called 'Initial transformation' and all it does is it adds the round key. Here the Plaintext is xored with the `w[0,3]`. This is done so that the key influences the encryption and decryption before confusion and diffusion.

###### Round 1-9
1. Substitute Bytes (Confusion)
	Every byte is replaced using S-Box. 
	The left most 4bits - row value
	The right most 4bits - column value
	
2. Shift Rows
	Rows are rotated left:
	- Row 0 → unchanged
    - Row 1 → shift left by 1
    - Row 2 → shift left by 2
    - Row 3 → shift left by 3
    
3. Mix Columns
	Avalanche effect - a crucial property where a tiny change in the input (plaintext or key) causes a drastic, significant change in the output (ciphertext or hash), ideally affecting about half the output bits.
	
4. Add Round Key
	XOR with the round's key. To add secrecy otherwise it would just be permutations of a matrix

Order of mix and shift doesnt matter
###### Round 10
All same steps except Mix Columns

#### Decryption:
| Encryption  | Decryption             |
| ----------- | ---------------------- |
| SubBytes    | InvSubBytes            |
| ShiftRows   | InvShiftRows           |
| MixColumns  | InvMixColumns          |
| AddRoundKey | AddRoundKey (same XOR) |
- Start with ciphertext
- Add **last round key**
- For rounds 9 → 1:
    - InvShiftRows
    - InvSubBytes
    - AddRoundKey
    - InvMixColumns
    
- Final round:
    - InvShiftRows
    - InvSubBytes
    - AddRoundKey

----
### Using AES in python
