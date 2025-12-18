# Infinite Series Manipulation Methods

Yuebo Hu, TA of MATH1560J, GC, SJTU

liuyejiang576@sjtu.edu.cn

November, 2025



## Exercises

1. Evaluate $S = \sum_{n=0}^{\infty} \frac{(-1)^n}{2n+1} = 1 - \frac{1}{3} + \frac{1}{5} - \frac{1}{7} + \cdots$
2. Evaluate $\sum_{n=1}^{\infty} \frac{n+1}{3^n}$.

3. Evaluate $\sum_{n=1}^{\infty} \frac{n^3}{2^n}$.

4. Evaluate $\sum_{k=0}^n \frac{\binom{n}{k}}{k+2}$.

5. Evaluate $\sum_{k=0}^n k^2 \binom{n}{k}$.

6. Evaluate $\sum_{n=0}^{\infty} \frac{1}{(2n+1)!}$.

7. Evaluate $\sum_{n=1}^{\infty} \frac{1}{n(n+1)} x^n$ and find its value at $x = 1$.



------

### Solution 1: Alternating Series with Odd Terms

Define: $$G(x) = \sum_{n=0}^{\infty} \frac{(-1)^n}{2n+1} x^{2n+1} = x - \frac{x^3}{3} + \frac{x^5}{5} - \frac{x^7}{7} + \cdots$$

We want $S = G(1)$.

Differentiate: $$G'(x) = \sum_{n=0}^{\infty} \frac{(-1)^n}{2n+1} \cdot (2n+1) x^{2n} = \sum_{n=0}^{\infty} (-1)^n x^{2n}$$

$$= 1 - x^2 + x^4 - x^6 + \cdots = \frac{1}{1+x^2}$$

Integrate: $$G(x) = \int_0^x \frac{1}{1+t^2},dt = \arctan(t)\Big|_0^x = \arctan(x)$$

Therefore: $$S = G(1) = \arctan(1) = \frac{\pi}{4}$$

------

### Solution 2: Geometric-Weighted Series with Shift

$$\sum_{n=1}^{\infty} \frac{n+1}{3^n} = \sum_{n=1}^{\infty} \frac{n}{3^n} + \sum_{n=1}^{\infty} \frac{1}{3^n}$$

From the standard formula: $\sum_{n=1}^{\infty} \frac{n}{3^n} = \frac{1/3}{(1-1/3)^2} = \frac{1/3}{4/9} = \frac{3}{4}$

And: $\sum_{n=1}^{\infty} \frac{1}{3^n} = \frac{1/3}{1-1/3} = \frac{1/3}{2/3} = \frac{1}{2}$

Therefore: $$\sum_{n=1}^{\infty} \frac{n+1}{3^n} = \frac{3}{4} + \frac{1}{2} = \frac{5}{4}$$

------

### Solution 3: Cubic Numerator

Start with $\sum_{n=0}^{\infty} x^n = \frac{1}{1-x}$

First derivative: $\sum_{n=1}^{\infty} nx^{n-1} = \frac{1}{(1-x)^2}$, so $\sum_{n=1}^{\infty} nx^n = \frac{x}{(1-x)^2}$

Second derivative: $\sum_{n=1}^{\infty} n^2x^{n-1} = \frac{1+x}{(1-x)^3}$, so $\sum_{n=1}^{\infty} n^2x^n = \frac{x(1+x)}{(1-x)^3}$

Third derivative: $$\frac{d}{dx}\left[\frac{x(1+x)}{(1-x)^3}\right] = \frac{(1+2x)(1-x)^3 + 3x(1+x)(1-x)^2}{(1-x)^6}$$

$$= \frac{(1-x)^2[(1+2x)(1-x) + 3x(1+x)]}{(1-x)^6} = \frac{(1+2x-x-2x^2) + 3x + 3x^2}{(1-x)^4}$$

$$= \frac{1 + 4x + x^2}{(1-x)^4}$$

Therefore: $\sum_{n=1}^{\infty} n^3 x^n = \frac{x(1+4x+x^2)}{(1-x)^4}$

At $x = 1/2$: $$\sum_{n=1}^{\infty} \frac{n^3}{2^n} = \frac{(1/2)(1 + 2 + 1/4)}{(1/2)^4} = \frac{(1/2)(13/4)}{1/16} = \frac{13/8}{1/16} = 26$$

------

### Solution 4: Binomial with Linear Denominator

$$\sum_{k=0}^n \frac{\binom{n}{k}}{k+2} = \sum_{k=0}^n \binom{n}{k} \int_0^1 x^{k+1},dx = \int_0^1 x \sum_{k=0}^n \binom{n}{k} x^k,dx$$

$$= \int_0^1 x(1+x)^n,dx$$

Let $u = 1+x$, then $du = dx$, and when $x=0$, $u=1$; when $x=1$, $u=2$:

$$= \int_1^2 (u-1)u^n,du = \int_1^2 (u^{n+1} - u^n),du$$

$$= \left[\frac{u^{n+2}}{n+2} - \frac{u^{n+1}}{n+1}\right]_1^2$$

$$= \frac{2^{n+2}}{n+2} - \frac{2^{n+1}}{n+1} - \frac{1}{n+2} + \frac{1}{n+1}$$

$$= \frac{2^{n+2}(n+1) - 2^{n+1}(n+2)}{(n+1)(n+2)} - \frac{(n+1) - (n+2)}{(n+1)(n+2)}$$

$$= \frac{2^{n+1}[2(n+1) - (n+2)] + 1}{(n+1)(n+2)} = \frac{2^{n+1} \cdot n + 1}{(n+1)(n+2)}$$

$$= \frac{n \cdot 2^{n+1} + 1}{(n+1)(n+2)}$$

------

### Solution 5: Squared Binomial Sum

Consider $G(x) = \sum_{k=0}^n k^2 \binom{n}{k} x^k$.

We know that $\frac{d}{dx}[(1+x)^n] = n(1+x)^{n-1}$, so: $$\sum_{k=0}^n k\binom{n}{k} x^{k-1} = n(1+x)^{n-1}$$

Multiply by $x$: $$\sum_{k=0}^n k\binom{n}{k} x^k = nx(1+x)^{n-1}$$

Differentiate again: $$\sum_{k=0}^n k^2\binom{n}{k} x^{k-1} = \frac{d}{dx}[nx(1+x)^{n-1}]$$

$$= n(1+x)^{n-1} + nx(n-1)(1+x)^{n-2} = n(1+x)^{n-2}[(1+x) + x(n-1)]$$

$$= n(1+x)^{n-2}[1 + nx]$$

Multiply by $x$: $$\sum_{k=0}^n k^2\binom{n}{k} x^k = nx(1+x)^{n-2}[1 + nx]$$

At $x=1$: $$\sum_{k=0}^n k^2\binom{n}{k} = n \cdot 2^{n-2} \cdot (1+n) = n(n+1)2^{n-2}$$

---

### Solution 6: Composite Substitution

Recall that $e^x = \sum_{n=0}^{\infty} \frac{x^n}{n!}$.

Consider: $$e^x = \sum_{n=0}^{\infty} \frac{x^n}{n!} = \sum_{n=0}^{\infty} \frac{x^{2n}}{(2n)!} + \sum_{n=0}^{\infty} \frac{x^{2n+1}}{(2n+1)!}$$

Similarly: $$e^{-x} = \sum_{n=0}^{\infty} \frac{(-x)^n}{n!} = \sum_{n=0}^{\infty} \frac{x^{2n}}{(2n)!} - \sum_{n=0}^{\infty} \frac{x^{2n+1}}{(2n+1)!}$$

Adding: $$e^x + e^{-x} = 2\sum_{n=0}^{\infty} \frac{x^{2n}}{(2n)!}$$

Subtracting: $$e^x - e^{-x} = 2\sum_{n=0}^{\infty} \frac{x^{2n+1}}{(2n+1)!}$$

Therefore: $$\sum_{n=0}^{\infty} \frac{x^{2n+1}}{(2n+1)!} = \frac{e^x - e^{-x}}{2} = \sinh(x)$$

At $x=1$: $$\sum_{n=0}^{\infty} \frac{1}{(2n+1)!} = \sinh(1) = \frac{e - e^{-1}}{2} = \frac{e^2 - 1}{2e}$$

------

### Solution 7: Harmonic-Like Series

Note that $\frac{1}{n(n+1)} = \frac{1}{n} - \frac{1}{n+1}$ (partial fractions).

$$G(x) = \sum_{n=1}^{\infty} \frac{x^n}{n(n+1)} = \sum_{n=1}^{\infty} \left(\frac{x^n}{n} - \frac{x^n}{n+1}\right)$$

$$= \sum_{n=1}^{\infty} \frac{x^n}{n} - \sum_{n=1}^{\infty} \frac{x^n}{n+1} = \sum_{n=1}^{\infty} \frac{x^n}{n} - \sum_{m=2}^{\infty} \frac{x^{m-1}}{m}$$

$$= \sum_{n=1}^{\infty} \frac{x^n}{n} - \frac{1}{x}\sum_{m=2}^{\infty} \frac{x^m}{m}$$

$$= \sum_{n=1}^{\infty} \frac{x^n}{n} - \frac{1}{x}\left(\sum_{m=1}^{\infty} \frac{x^m}{m} - x\right)$$

$$= \sum_{n=1}^{\infty} \frac{x^n}{n} - \frac{1}{x}\sum_{m=1}^{\infty} \frac{x^m}{m} + 1$$

Since $\sum_{n=1}^{\infty} \frac{x^n}{n} = -\ln(1-x)$:

$$G(x) = -\ln(1-x) + \frac{\ln(1-x)}{x} + 1 = 1 + \frac{\ln(1-x)}{x}(1-x)$$

At $x = 1$ (using L'Hôpital's rule): $$G(1) = 1 + \lim_{x \to 1} \frac{\ln(1-x)(1-x)}{x} = 1 + 0 = 1$$

Therefore: $\sum_{n=1}^{\infty} \frac{1}{n(n+1)} = 1$

---





