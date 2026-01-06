The Chinese Remainder Theorem (CRT) is a number theory principle that finds a unique integer solution (or remainder) for a system of simultaneous congruences, provided the divisors (moduli) are pairwise co-prime.

```
from math import prod

def crt(remainders, moduli):
#Number of remainder == Number of moduli
    M = prod(moduli)
    x = 0

    for a, m in zip(remainders, moduli):
        Mi = M // m
        yi = pow(Mi, -1, m)   # modular inverse
        x += a * Mi * yi

    return x % M
    
remainder = list(input("Enter remainders: "))
moduli = list(input("Enter moduli: "))
```