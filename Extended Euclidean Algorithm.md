It is a way to find the coefficient (x,y) for [[Bézout's identity]] ` ax + by = gcd(a,b)`.
```
def inverse_multiplicative_mod(a,b):

	if b == 0:
		return a, 1, 0

	gcd, x1, y1 = inverse_multiplicative_mod(b,a%b)
	x = y1
	y = x1 - y1 * (a//b)
	return d, x, y //bezouts co-efficients
	
```
>[!Note] Do x%n since x can be a negative number.

---

>[!Info] Modular Multiplicative Inverse exits only if two numbers are co-prime.

It is used to find modular multiplicative inverse of a number under (mod n). 
Using [[Bézout's identity]] we know  `ax + by = gcd(a,b)`. It is the x value when `gcd(a,b) = 1`.

In `ax + by = gcd(a,b)` - only if `gcd(a,b)` = 1, ie they are relatively co-prime, does 
`x = a^-1 (mod N)`. 

In to find the modular multiplicative inverse, similar to the columns in [[Euclidean Algorithm]] we use in this, but with the extensions of T1, T2 and T. Where T1 =0 and T2 = 1 in the first iteration and T = T1 -T2 * Q. Then T1 will be the modular multiplicative inverse under (mod n) when there is no more division possible. You stop similar to Euclidian algorithm, when B = 0.

![[EEA_NexusAcademy.png]]





