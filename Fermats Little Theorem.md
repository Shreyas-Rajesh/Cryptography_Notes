In number theory, **Fermat's little theorem** states that if p is a prime number, then for any integer a, the number a^p − a is an integer multiple of p.	
	${\displaystyle a^{p}\equiv a{\pmod {p}}.}$

This is the special case of [[Eulers - Fermats theorem]]
##### *Real world application:* 
For the question: 2^502 (mod 5)
	${  \textbf{Given:}\quad 5 \text{ is prime, and } \gcd(2,5)=1.  }$

Fermat's Little Theorem states that for a prime (p) and integer (a) with ${p\nmid a}$,  
	${  a^{p-1}\equiv 1 \pmod p. }$

With (p=5) this gives (a^{4}\equiv 1\pmod 5) for any (a) not divisible by (5). In particular,  
	${ 2^{4}\equiv 1 \pmod 5.}$

Now write the exponent (502) as a multiple of (4) plus a remainder:  
	${502 = 4\cdot 125 + 2. }$

So  ${2^{502} = 2^{4\cdot 125 + 2} = \bigl(2^{4}\bigr)^{125}\cdot 2^{2}.}$

Reduce modulo (5) using ${2^{4}\equiv 1\pmod 5}$:  
	${2^{502}\equiv 1^{125}\cdot 2^{2}\equiv 2^{2}\pmod 5. }$

Finally compute (2^{2}=4), so  ${2^{502}\equiv 4 \pmod 5. }$

$\boxed{2^{502}\equiv 4 \pmod 5}$

---

#### .
If `gcd(a,p) = 1`  then 
	${\displaystyle a^{p-1}\equiv 1{\pmod {p}}.}$

