Let's say we're given an RSA public key (N, e) and two ciphertexts C1 and C2, and the plaintexts are M1 and M2 satisfying M1 = a(M2) + b (mod N).
We can then recover M1 and M2 by launching a Franklin-Reiter Attack:
```
# Code written in SageMath:
PRx.<xn> = PolynomialRing(ZmodN)
x = PRx.gen()
f = (ax + b)**e - C1
g = x**e - C2
```
M2 is a root of polynomials f and g hence we can just find the GCD. If it is linear, then its root is M2. 

```
while g:
    f,g = g,f % g
m = f.monic()
-m[0]
```

M1 can then be found by subsitituting in the earlier equation.



