Encoding is the process of converting data from one form to another. Considering that different systems speak different "languages" through encoding you can make sure that no data is lost in-between their talk.
###### ***Bytes**
8 bits is one byte. 
Common things to remember: 1024 bits is 128bytes, 512 is 64bytes, 256bits is 32bytes,126bits is 16bytes
###### ***ASCII***
ASCII is a 7-bit encoding that which allows the representation of text using the integers 0-127. 
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
Implementation
#### bytes
1. `b" "` - to convert a string into bytes. Only ASCII valid characters should be in the string.
2. `bytes.fromhex()` - to convert a hex value into bytes
3. `bytes()` 
	1. `bytes(s,"what_encoding_of_s")` - convert s into bytes()
	2. `bytes(n)` - convert "n" integer to byte value.
	3. `bytes(l)` - converts "l" list values into bytes.
4. `bytearray()` - A bytearray is a mutable sequence of bytes. It is a data structure designed to store a collection of 8-bit values.
5. `encode()` - To convert a string "s" into bytes.
	1. `(errors=_errors_)` - Choose how to handle the errors.
		1.  `ignore` : ignores the characters that cannot be encoded
		2. `nameplace` : replaces the character with a text explaining the character ("{LATIN SMALL LETTER A WITH RING ABOVE}")
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