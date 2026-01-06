Denoted as ${\phi (n)}$ , the function shows the *number of positive integers less than 'n'  that are co-prime to n*.
i.e, the number of positive integers, less than n, where `gcd(n,[number less than n]) = 1`

To compute this: 
1. If "n" is a prime:
	${\phi(n) = (n-1)}$

2. If ${n = p \times q}$, where *p and q* are primes
	${\phi(n) = (p-1) \times (q-1)}$

3. If ${n = a \times b}$, where *Either a or b is composite, or both*.
	${\phi (n) = n \times (1 - \frac{1}{P1}) \times (1- \frac{1}{P2}) .. ..}$
	
	Consider ${\phi (1000)}$, we can write 1000 as ${2^3 \times 5^3}$ (Factorising to the core simplifies it into primes)
	Since we have two primes P1 = 2 and P2 = 5, use the function.
	
