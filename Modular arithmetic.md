For integers a, b, n:  `a ≡ b (mod n)` means:

- `n | (a - b)` - expand with the remainder formula to prove
- a % n = b % n

---
Basic Properties

If ${ a \equiv b \pmod{n} }$ and ${ c \equiv d \pmod{n} }$, then:
1. Addition:
	${ a + c \equiv b + d \pmod{n} }$
2. Subtraction:
	${ a - c \equiv b - d \pmod{n} }$
3. Multiplication:
	${ ac \equiv bd \pmod{n} }$
4. Exponentiation:
	${ a^k \equiv b^k \pmod{n} }$
5. Negative numbers example:
	${ -3 \equiv 4 \pmod{7} }$
	because -3 % 7 = 4

---
Reductions
Any number can be replaced with its remainder:
	${ a \equiv a \bmod n \pmod{n} }$
Here `a mod n` means the remainder that `a/n` leaves, let that be r. Also we know 
${a = n \times q + r}$, so `a - r = n * q`. (bullet point 1)

---
Multiplicative Inverse
The modular inverse of a modulo n is a number a^-1 such that:
	${ a a^{-1} \equiv 1 \pmod{n} }$

Note : The inverse exists if ${ \gcd(a, n) = 1 }$

---
Linear Congruence
General form: ${ ax \equiv b \pmod{n} }$
Here : ax - b = k * (mod n) -> ax -k (mod n) = b

Steps:
1. Compute g = gcd(a, n)
2. If g does not divide b -> no solution
3. If g = 1:
   ${ x \equiv b \cdot a^{-1} \pmod{n} }$
4. If g > 1:
   Divide equation by g, giving g solutions modulo n

---

Replacing numbers by remainders:

23 * 87 (mod 10)

23 ≡ 3 (mod 10)
87 ≡ 7 (mod 10)

${ 3 \cdot 7 = 21 \equiv 1 \pmod{10} }$

Cancellation Rule:
You may cancel a in: ${ a k \equiv a m \pmod{n} }$
only if: ${ \gcd(a, n) = 1 }$ (multiply by the inverse)

Negative modulo: ${ -17 \bmod 5 = 3 }$
because ${ -17 \equiv 3 \pmod{5} }$
