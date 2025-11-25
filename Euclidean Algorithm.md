### To find the GCD (HCF). 
GCD - take a list of divisors that gives reminder 0, out of that take the common divisors for both numbers. The hight value among the common divisors is GCD.

> [!example]
> 12 and 33
> 12 : *1* ,2 ,*3*, 4 ,6 ,12
> 33 : *1* ,*3* ,11 ,33
> Highest common one: 3

>[!note] GCD will be prime for 2 different prime numbers (co-prime numbers)

`a = bq + r, gcd(a,b) = gcd(b,r) - if 0 <= r< b, where r = a (mod b)`

Implementing GCD using euclidean algorithm:
Consider two values A and B then the gcd(A, B) will be the value in A when the B value is zero after - 
1. Divide A/B
2. Find the remainder 
3. The A = B and B = remainder in the next step

> [!example] GCD (12,33)
> 1. A = 33, B = 12, Remainder = 9, Quotient = 2
> 2. A = 33, B = 9, R = 3
> 3. A = 9, B = 3, R =0
> 4. A = 3, B = 0
> Here A = 3 when B = 0
> ***GCD(A,B) = 3***

```
import math
math.gcd(A,B) //will give 0 if both values are 0

def gcd(a,b):
	if b == 0:
		return a
	return gcd(b,a%b)
```


