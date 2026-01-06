Encoding is the process of converting data from one form to another. Considering that different systems speak different "languages" through encoding you can make sure that no data is lost in-between their talk.

###### ***Integer**
Integers are whole numbers.
- **Signed integers**  
    Can represent positive and negative values. 
    MSB becomes 1 showings its negetive.
    
- **Unsigned integers**  
    Represent only non-negative values (0 and above).  
    Allow a larger positive range for the same number of bytes.
    
- **Endianness**  
    Defines how multi-byte integers are stored in memory.
    - **Big-endian**: Most significant byte comes first.
    - **Little-endian**: Least significant byte comes first.  
        This matters when converting integers to/from bytes.

###### ***Bytes**
8 bits is one byte. 
Common things to remember: 1024 bits is 128bytes, 512 is 64bytes, 256bits is 32bytes,126bits is 16bytes
###### ***ASCII***
ASCII is a 7-bit encoding that which allows the representation of text using the integers 0-127. 
###### ***UTF***
UTF - 8: Variable-length encoding (1–4 bytes)., Backward-compatible with ASCII (0–127 same values), Most widely used encoding today.

UTF-16: Uses mostly 2 bytes, sometimes 4 bytes, Not ASCII-compatible.
UTF - 32: Fixed 4 bytes per character.
###### ***Base64***
*Valid characters in base64 :*
- 26 uppercase letters
- 26 lowercase letters
- 10 numbers
- + and / for new lines
###### ***Hexadecimal***
It is represented as `\x00` (it is one byte, so each char represents half byte (nibble)). 
Valid characters:
- 0 - 9
- a - f

--- 
#### bytes
1. `b" "` - to convert a string into bytes. Only ASCII valid characters should be in the string.
2. `bytes.fromhex()` - to convert a hex string into bytes
3. `bytes()` 
	1. `bytes(s,"what_encoding_of_s")` - convert s into bytes()
	2. `bytes(n)` - create "n" number of null bytes
	3. `bytes(l)` - converts "l" list values into bytes.
4. `bytearray()` - A bytearray is a mutable sequence of bytes. It is a data structure designed to store a collection of 8-bit values.
5. `encode()` - To convert a string "s" into bytes.
	1. `(errors=_errors_)` - Choose how to handle the errors.
		1.  `ignore` : ignores the characters that cannot be encoded
		2. `namreplace` : replaces the character with a text explaining the character ("{LATIN SMALL LETTER A WITH RING ABOVE}")
		3. `strict` : Default, raises an error on failure
		4. `replace`: replaces the character with a question mark.
6. `long_to_bytes()` - to convert long integers into bytes
	1. `long_to_bytes(n,bytesize = k)` - forces the byte size to be k

#### Base64
Import module name: `base64`
1. `base64.b64encode('ascii')` - to encode ascii characters as b64
2. `base64.b64decode('base64')` - to decode base64 values
Note similar to this there is `b32`, `b16`
Each Base64 character represents 6 bits of data.

#### Hex
1. `hex(x)` - to convert integer value 'x' into its hex value
2. `b.hex()` - to convert byte value 'b' into its hex value
Note to convert string, we usually use this


#### Integer
- `int.from_bytes(b, byteorder)` – Converts bytes `b` into an integer.
    - `byteorder` : `"big"` or `"little"`
- `n.to_bytes(length, byteorder)` – Converts integer `n` into bytes of size `length`.
    - `byteorder` : `"big"` or `"little"`
- `int(x)` – Converts `x` into an integer (works for strings, floats, booleans, etc.)
- `hex(x)` – Converts integer `x` into its hexadecimal string representation.
- `bin(x)` – Converts integer `x` into its binary string representation.
- `oct(x)` – Converts integer `x` into its octal string representation.
- `long_to_bytes(n, bytesize=k)` – Converts long integers into bytes (from `Crypto.Util.number`).
    - Optional `bytesize` forces fixed byte length.

