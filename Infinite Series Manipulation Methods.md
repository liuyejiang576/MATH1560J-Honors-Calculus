# Infinite Series Manipulation Methods

Yuebo Hu, TA of MATH1560J, GC, SJTU

liuyejiang576@sjtu.edu.cn

November, 2025



> "The infinite! No other question has ever moved so profoundly the spirit of man."
>
> — **David Hilbert**

## 1. Introduction

You've just learned about power series: infinite sums of the form $\sum_{n=0}^{\infty} a_n x^n$. Now we'll explore a powerful technique that converts discrete summation to continuous functions.

**The key insight:** Instead of wrestling with a sequence ${a_0, a_1, a_2, \ldots}$ directly, we can encode the entire sequence into a single function: 

$$G(x) = \sum_{n=0}^{\infty} a_n x^n = a_0 + a_1 x + a_2 x^2 + \cdots$$

We treat it as **formal power series**. We manipulate it algebraically **without worrying about convergence**. The variable $x$ is just a placeholder that helps us track coefficients.

Why does this help? Because:

1. **Algebraic operations on functions** (addition, multiplication, differentiation) correspond to **useful operations on sequences**
2. **Difficult discrete problems** often become **routine calculus problems**
3. We can take advantage of everything we know about functions (derivatives, integrals, partial fractions) to extract information about sequences



## 2. Common Sequences

| Sequence ${a_n}$                                             | Description     | $G(x)$              | Derivation                                        |
| ------------------------------------------------------------ | --------------- | ------------------- | ------------------------------------------------- |
| ${1, 1, 1, \ldots}$                                          | Constant        | $\frac{1}{1-x}$     | Geometric series: $\sum_{n=0}^{\infty} x^n$       |
| ${0, 1, 2, 3, \ldots}$                                       | Natural numbers | $\frac{x}{(1-x)^2}$ | Differentiate $\frac{1}{1-x}$ and multiply by $x$ |
| ${1, q, q^2, q^3, \ldots}$                                   | Geometric       | $\frac{1}{1-qx}$    | Geometric series with ratio $qx$                  |
| ${1, 0, 1, 0, 1, \ldots}$                                    | Alternating     | $\frac{1}{1+x^2}$   | Only even powers: $\sum_{n=0}^{\infty} x^{2n}$    |
| $\binom{n}{0}, \binom{n}{1}, \ldots, \binom{n}{n}, 0, 0, \ldots$ | Binomial        | $(1+x)^n$           | Binomial theorem                                  |



## 3. Operational Properties

Let $G(x) = \sum_{n=0}^{\infty} a_n x^n$ and $H(x) = \sum_{n=0}^{\infty} b_n x^n$.

1. Addition: $$G(x) + H(x) = \sum_{n=0}^{\infty} (a_n + b_n) x^n$$ 

2. Scalar Multiplication: $$c \cdot G(x) = \sum_{n=0}^{\infty} (c \cdot a_n) x^n$$

3. Multiplication (Cauchy Product) (convolution): $$G(x) \cdot H(x) = \sum_{n=0}^{\infty} \left(\sum_{k=0}^{n} a_k b_{n-k}\right) x^n$$ 

4. Differentiation: $$\frac{d}{dx}G(x) = \sum_{n=1}^{\infty} n a_n x^{n-1} = \sum_{n=0}^{\infty} (n+1) a_{n+1} x^n$$ 

*Interpretation:* Multiplies the $n$-th term by $n$ and shifts indices.

5. Integration:$$\int_0^x G(t),dt = \sum_{n=0}^{\infty} \frac{a_n}{n+1} x^{n+1} = \sum_{n=1}^{\infty} \frac{a_{n-1}}{n} x^n$$ 

*Interpretation:* Divides the $n$-th term by $n+1$ and shifts indices.

6. Substitution: $$G(cx) = \sum_{n=0}^{\infty} a_n (cx)^n = \sum_{n=0}^{\infty} (c^n a_n) x^n$$ 

*Interpretation:* Multiplies the $n$-th term by $c^n$.



## 4. Example: Fibonacci Sequence

The Fibonacci sequence is defined by $F_0 = 0$, $F_1 = 1$, and $F_n = F_{n-1} + F_{n-2}$ for $n \geq 2$. Find a closed-form expression for $F_n$.

Construct $$F(x) = \sum_{n=0}^{\infty} F_n x^n = 0 + x + x^2 + 2x^3 + 3x^4 + 5x^5 + \cdots$$

For $n \geq 2$: $F_n = F_{n-1} + F_{n-2}$

$$\sum_{n=2}^{\infty} F_n x^n = \sum_{n=2}^{\infty} F_{n-1} x^n + \sum_{n=2}^{\infty} F_{n-2} x^n$$

The left side is: $$F(x) - F_0 - F_1 x = F(x) - x$$

The first term on the right is: $$x \sum_{n=2}^{\infty} F_{n-1} x^{n-1} = x \sum_{m=1}^{\infty} F_m x^m = x(F(x) - F_0) = xF(x)$$

The second term on the right is: $$x^2 \sum_{n=2}^{\infty} F_{n-2} x^{n-2} = x^2 \sum_{k=0}^{\infty} F_k x^k = x^2 F(x)$$

$F(x) - x = xF(x) + x^2 F(x)$,  $F(x) = \frac{x}{1-x-x^2}$

$1 - x - x^2 = (1-\varphi x)(1-\psi x)$ where $\varphi = \frac{1+\sqrt{5}}{2}$ and $\psi = \frac{1-\sqrt{5}}{2}$.

$$F(x) = \frac{1}{\sqrt{5}} \left(\frac{1}{1-\varphi x} - \frac{1}{1-\psi x}\right)$$

$$\frac{1}{1-\varphi x} = \sum_{n=0}^{\infty} \varphi^n x^n, \quad \frac{1}{1-\psi x} = \sum_{n=0}^{\infty} \psi^n x^n$$

Therefore: $$F(x) = \frac{1}{\sqrt{5}} \sum_{n=0}^{\infty} (\varphi^n - \psi^n) x^n$$

Comparing coefficients: $$F_n = \frac{1}{\sqrt{5}}(\varphi^n - \psi^n) = \frac{1}{\sqrt{5}}\left[\left(\frac{1+\sqrt{5}}{2}\right)^n - \left(\frac{1-\sqrt{5}}{2}\right)^n\right]$$

Remark: Our method transforms a recurrence relation into an algebraic equation, which we can solve using standard techniques.



## 5. Example: Alternating Harmonic Series

Evaluate $S = \sum_{n=1}^{\infty} \frac{(-1)^{n-1}}{n} = 1 - \frac{1}{2} + \frac{1}{3} - \frac{1}{4} + \frac{1}{5} - \cdots$

Define: $$G(x) = \sum_{n=1}^{\infty} \frac{(-1)^{n-1}}{n} x^n = x - \frac{x^2}{2} + \frac{x^3}{3} - \frac{x^4}{4} + \cdots$$

Our goal is to find $S = G(1)$.

$$G'(x) = \sum_{n=1}^{\infty} \frac{(-1)^{n-1}}{n} \cdot n x^{n-1} = \sum_{n=1}^{\infty} (-1)^{n-1} x^{n-1}$$

$$= 1 - x + x^2 - x^3 + \cdots = \sum_{n=0}^{\infty} (-x)^n = \frac{1}{1-(-x)} = \frac{1}{1+x}$$

(This is valid for $|x| < 1$.)

$$G(x) = \int_0^x \frac{1}{1+t}\,dt = \ln(1+t)\Big|_0^x = \ln(1+x)$$

$$S = G(1) = \ln(1+1) = \ln 2$$

**Verification:** $\ln 2 \approx 0.693147$, and partial sums confirm: $1 - 0.5 + 0.333... - 0.25 + \cdots \approx 0.693$.

Remark: Differentiate to simplify, integrate to recover. 



## 6. Example: Geometric-Weighted Series

Evaluate $\sum_{n=1}^{\infty} \frac{n}{2^n}$.

Consider: $$G(x) = \sum_{n=1}^{\infty} n x^n$$,  We want to find $G(1/2)$.

$$G(x) = x \sum_{n=1}^{\infty} n x^{n-1}$$,  considering $$\frac{d}{dx}\left(x^n\right) = nx^{n-1}$$

So: $$\sum_{n=1}^{\infty} nx^{n-1} = \frac{d}{dx}\left(\sum_{n=1}^{\infty} x^n\right) = \frac{d}{dx}\left(\frac{x}{1-x}\right) = \frac{1}{(1-x)^2}$$,  $$G(x) = \frac{x}{(1-x)^2}$$

$$\sum_{n=1}^{\infty} \frac{n}{2^n} = G(1/2) = \frac{1/2}{(1-1/2)^2} = \frac{1/2}{(1/2)^2} = \frac{1/2}{1/4} = 2$$

Remark: The operations of differentiation and integration provide a powerful generalization of the high school "misalignment subtraction" method. Multiply the series by the common ratio and subtracting to create a telescoping sum is exactly analogous to our approach where differentiation handles the "n" multiplier and algebraic manipulation simplifies the series. The differentiation step in generating functions corresponds to the index shift in misalignment subtraction, while the algebraic solution for $S$ is equivalent to solving the equation derived from the generating function.



## 7. Example: Sum with Quadratic Numerator

Evaluate $\sum_{n=1}^{\infty} \frac{n^2}{2^n}$.

We'll build on the previous example, using differentiation twice.

Start with the basic geometric series $$\sum_{n=0}^{\infty} x^n = \frac{1}{1-x}$$

The first differentiation gives$$\sum_{n=1}^{\infty} nx^n = \frac{x}{(1-x)^2}$$

Differentiate again, $$\frac{d}{dx}\left(\sum_{n=1}^{\infty} nx^n\right) = \sum_{n=1}^{\infty} n^2 x^{n-1}$$

$$\frac{d}{dx}\left(\frac{x}{(1-x)^2}\right) = \frac{(1-x)^2 - x \cdot 2(1-x)(-1)}{(1-x)^4} = \frac{(1-x)^2 + 2x(1-x)}{(1-x)^4}$$

$$= \frac{(1-x)(1-x+2x)}{(1-x)^4} = \frac{1+x}{(1-x)^3}$$

Then, $$\sum_{n=1}^{\infty} n^2 x^n = \frac{x(1+x)}{(1-x)^3}$$

Substitute $x = 1/2$,  $$\sum_{n=1}^{\infty} \frac{n^2}{2^n} = \frac{(1/2)(1 + 1/2)}{(1-1/2)^3} = \frac{(1/2)(3/2)}{(1/2)^3} = \frac{3/4}{1/8} = 6$$

Remark: The pattern is clear: each differentiation and multiplication by $x$ increases the power of $n$ in the numerator. This technique generalizes to $\sum \frac{n^k}{2^n}$ for any positive integer $k$. The formula $\frac{x(1+x)}{(1-x)^3}$ shows the structure: as we go from linear to quadratic terms, the denominator's degree increases.



## 8. Example: Sum of Reciprocals with Binomial Coefficients

Evaluate $\sum_{k=0}^n \frac{\binom{n}{k}}{k+1}$.

Recall that $\frac{1}{k+1} = \int_0^1 x^k  \, dx$. Therefore: $\sum_{k=0}^n \frac{\binom{n}{k}}{k+1} = \sum_{k=0}^n \binom{n}{k} \int_0^1 x^k  \, dx = \int_0^1 \sum_{k=0}^n \binom{n}{k} x^k  \, dx$

Recognize binomial expansion,  $= \int_0^1 (1+x)^n dx = \left[\frac{(1+x)^{n+1}}{n+1}\right]_0^1 = \frac{2^{n+1} - 1}{n+1}$

**Verification:** For $n=2$: $\frac{\binom{2}{0}}{1} + \frac{\binom{2}{1}}{2} + \frac{\binom{2}{2}}{3} = 1 + 1 + \frac{1}{3} = \frac{7}{3} = \frac{2^3-1}{3} = \frac{7}{3} \quad \checkmark$

Remark: The identity $\frac{1}{k+1} = \int_0^1 x^k  \, dx$ transforms a difficult sum into a simple integral. This technique is useful whenever denominators involve $k+a$ for constant $a$.



## 9. Summary

**Encode your sequence, manipulate the function, decode the result**.

| Problem Type            | Technique               | Example                                  |
| ----------------------- | ----------------------- | ---------------------------------------- |
| Sum of sequence         | Direct substitution     | $\sum \binom{n}{k} = 2^n$                |
| Weighted sum with $n$   | Differentiation         | $\sum n a_n x^{n-1}$ from $\sum a_n x^n$ |
| Reciprocals of integers | Integration             | $\sum \frac{x^n}{n}$ from $\sum x^n$     |
| Products/convolutions   | Multiplication of GFs   | $\sum_{k=0}^n a_k b_{n-k}$               |
| Recurrence relations    | Algebraic equations     | Fibonacci: $F = x + xF + x^2F$           |
| Alternating series      | Substitute $x = -1$     | $\sum (-1)^k \binom{n}{k}$               |
| Geometric weights       | Substitute specific $x$ | $\sum \frac{a_n}{2^n}$ with $x=1/2$      |

Quick Reference Formulas

$\sum_{n=0}^{\infty} x^n = \frac{1}{1-x}$

$\sum_{n=0}^{\infty} nx^{n-1} = \frac{1}{(1-x)^2}$

$\sum_{n=1}^{\infty} nx^n = \frac{x}{(1-x)^2}$

$\sum_{n=1}^{\infty} n^2x^n = \frac{x(1+x)}{(1-x)^3}$

$\sum_{n=0}^{\infty} \frac{x^n}{n!} = e^x$

$\sum_{n=1}^{\infty} \frac{x^n}{n} = -\ln(1-x)$

$\sum_{n=1}^{\infty} \frac{(-1)^{n-1}x^n}{n} = \ln(1+x)$



## 11. Exercises

1. Evaluate $S = \sum_{n=0}^{\infty} \frac{(-1)^n}{2n+1} = 1 - \frac{1}{3} + \frac{1}{5} - \frac{1}{7} + \cdots$

2. Evaluate $\sum_{n=1}^{\infty} \frac{n+1}{3^n}$.

3. Evaluate $\sum_{n=1}^{\infty} \frac{n^3}{2^n}$.

4. Evaluate $\sum_{k=0}^n \frac{\binom{n}{k}}{k+2}$.

5. Evaluate $\sum_{k=0}^n k^2 \binom{n}{k}$.

6. Evaluate $\sum_{n=0}^{\infty} \frac{1}{(2n+1)!}$.

7. Evaluate $\sum_{n=1}^{\infty} \frac{1}{n(n+1)} x^n$ and find its value at $x = 1$.



## Appendix: Other Methods (Not Required)

The summation of infinite series characterizes a vast variety of methods. Even if neither of the following methods would be desirable in the MATH1560J Examination, an acquaintance with them would hopefully make a difference in your future path of maths study.

 

### 1. Infinite Products

**Key Observation:** The zeros of $\sin x$ are $x = 0, \pm\pi, \pm 2\pi, \pm 3\pi, \ldots$

Just as a polynomial can be written as a product of its linear factors, Euler boldly proposed that:

$$\sin x = x\left(1 - \frac{x}{\pi}\right)\left(1 + \frac{x}{\pi}\right)\left(1 - \frac{x}{2\pi}\right)\left(1 + \frac{x}{2\pi}\right)\cdots$$

Pairing positive and negative roots:

$$\sin x = x\left(1 - \frac{x^2}{\pi^2}\right)\left(1 - \frac{x^2}{4\pi^2}\right)\left(1 - \frac{x^2}{9\pi^2}\right)\cdots$$

**Theorem (Euler's Infinite Product for Sine):** $$\boxed{\sin x = x \prod_{n=1}^{\infty}\left(1 - \frac{x^2}{n^2\pi^2}\right)}$$



### 2. Wallis Product

Setting $x = \frac{\pi}{2}$ in the infinite product for sine:

$$\sin\frac{\pi}{2} = \frac{\pi}{2}\prod_{n=1}^{\infty}\left(1 - \frac{\pi^2/4}{n^2\pi^2}\right) = \frac{\pi}{2}\prod_{n=1}^{\infty}\left(1 - \frac{1}{4n^2}\right)$$

Since $\sin\frac{\pi}{2} = 1$:

$$1 = \frac{\pi}{2}\prod_{n=1}^{\infty}\frac{4n^2 - 1}{4n^2} = \frac{\pi}{2}\prod_{n=1}^{\infty}\frac{(2n-1)(2n+1)}{(2n)^2}$$

Rearranging:

$$\frac{\pi}{2} = \prod_{n=1}^{\infty}\frac{(2n)^2}{(2n-1)(2n+1)} = \frac{2}{1} \cdot \frac{2}{3} \cdot \frac{4}{3} \cdot \frac{4}{5} \cdot \frac{6}{5} \cdot \frac{6}{7} \cdots$$

**Theorem (Wallis Product):** $$\boxed{\frac{\pi}{2} = \prod_{n=1}^{\infty}\frac{4n^2}{4n^2-1} = \frac{2 \cdot 2 \cdot 4 \cdot 4 \cdot 6 \cdot 6 \cdot 8 \cdot 8 \cdots}{1 \cdot 3 \cdot 3 \cdot 5 \cdot 5 \cdot 7 \cdot 7 \cdot 9 \cdots}}$$

This beautiful formula expresses the transcendental number $\pi$ entirely in terms of integers!



### 3. The Basel Problem

Evaluate $\displaystyle\sum_{n=1}^{\infty} \frac{1}{n^2} = 1 + \frac{1}{4} + \frac{1}{9} + \frac{1}{16} + \cdots$

This problem, posed in 1644, remained unsolved until Euler tackled it in 1734.

**Euler's Solution:**

Consider the function $f(x) = \frac{\sin x}{x}$. From the Taylor series: $\frac{\sin x}{x} = 1 - \frac{x^2}{3!} + \frac{x^4}{5!} - \frac{x^6}{7!} + \cdots$

From the infinite product formula: $\frac{\sin x}{x} = \prod_{n=1}^{\infty}\left(1 - \frac{x^2}{n^2\pi^2}\right)$

Let $w = x^2$. Expanding the product (keeping only terms up to $w$):

$$= 1 - w\left(\frac{1}{\pi^2} + \frac{1}{4\pi^2} + \frac{1}{9\pi^2} + \cdots\right) + O(w^2)$$

$$= 1 - \frac{w}{\pi^2}\left(1 + \frac{1}{4} + \frac{1}{9} + \cdots\right) + O(w^2)$$

**Matching coefficients of $w$:**

$$-\frac{1}{6} = -\frac{1}{\pi^2}\sum_{n=1}^{\infty}\frac{1}{n^2}$$

**Theorem (Basel Problem):** $$\boxed{\sum_{n=1}^{\infty} \frac{1}{n^2} = \frac{\pi^2}{6}}$$



### 4. Higher Powers

**Definition:** For $s > 1$, the Riemann zeta function is: $$\zeta(s) = \sum_{n=1}^{\infty} \frac{1}{n^s}$$

Euler's method extends to higher even powers!

**From the infinite product expansion:**

Consider the sum of products of pairs of roots: $$\sum_{j<k} \frac{1}{w_j w_k}$$

where $w_j = j^2\pi^2$ are the roots of $\frac{\sin x}{x} = 0$ (excluding $x=0$).

From the identity: $$\left(\sum_{k=1}^{\infty} \frac{1}{w_k}\right)^2 = \sum_{k=1}^{\infty} \frac{1}{w_k^2} + 2\sum_{j<k}\frac{1}{w_j w_k}$$

We can extract the coefficient of $w^2$ in the product expansion to find: $$\sum_{j<k}\frac{1}{w_j w_k} = \frac{1}{5!}$$

Therefore: $$\sum_{k=1}^{\infty}\frac{1}{w_k^2} = \left(\frac{1}{3!}\right)^2 - 2 \cdot \frac{1}{5!} = \frac{1}{36} - \frac{2}{120} = \frac{1}{36} - \frac{1}{60} = \frac{1}{90}$$

Since $w_k = k^2\pi^2$: $$\frac{1}{\pi^4}\sum_{k=1}^{\infty}\frac{1}{k^4} = \frac{1}{90}$$

**Theorem:** $$\boxed{\zeta(4) = \sum_{n=1}^{\infty} \frac{1}{n^4} = \frac{\pi^4}{90}}$$

**General Results for Even Powers:**

$\zeta(2) = \frac{\pi^2}{6}$,  $\zeta(4) = \frac{\pi^4}{90}$,  $\zeta(6) = \frac{\pi^6}{945}$,  $\zeta(8) = \frac{\pi^8}{9450}$
$\zeta(10) = \frac{\pi^{10}}{93555}$,  $\zeta(12) = \frac{691\pi^{12}}{638512875}$

For odd powers like $\zeta(3)$, no closed form involving elementary constants is known. The value $\zeta(3) = 1.202056903...$ is called Apéry's constant.



## 5. Fourier Series

This section may help you understand some problems in Homework 6 better. Further clarifications and useful applications will be covered later if time permits.

We can express a periodic function $f(x)$ with period $2\pi$ as: $$f(x) = \frac{a_0}{2} + \sum_{k=1}^{\infty}\left(a_k\cos(kx) + b_k\sin(kx)\right)$$

The trigonometric functions ${\cos(kx), \sin(kx)}$ are **orthogonal** on $[0, 2\pi]$:

 $$ \int_{0}^{2\pi} \cos(mx) \cos(nx) dx = \begin{cases} 0 & m \neq n \\ \pi & m = n \neq 0 \\ 2\pi & m = n = 0 \end{cases} $$ 

 $$ \int_{0}^{2\pi} \sin(mx) \sin(nx) dx = \begin{cases} 0 & m \neq n \\ \pi & m = n \end{cases} $$

 $$ \int_{0}^{2\pi} \sin(mx) \cos(nx) dx = 0 \quad \text{for all } m, n $$

To find $a_0$, integrate both sides of the series: $$\int_0^{2\pi} f(x)  \, dx = \int_0^{2\pi} \frac{a_0}{2}  \, dx + \sum_{k=1}^{\infty}\int_0^{2\pi}\left(a_k\cos(kx) + b_k\sin(kx)\right)dx$$

Since $\int_0^{2\pi}\cos(kx)  \, dx = 0$ and $\int_0^{2\pi}\sin(kx)  \, dx = 0$ for $k \geq 1$:

$$\int_0^{2\pi} f(x)   \, dx = \frac{a_0}{2} \cdot 2\pi = \pi a_0$$

Therefore: $$a_0 = \frac{1}{\pi}\int_0^{2\pi} f(x)  \, dx$$

To find $a_n$ for $n \geq 1$, multiply both sides by $\cos(nx)$ and integrate: $$\int_0^{2\pi} f(x)\cos(nx)  \, dx = \frac{a_0}{2}\int_0^{2\pi}\cos(nx)  \, dx + \sum_{k=1}^{\infty}a_k\int_0^{2\pi}\cos(kx)\cos(nx)  \, dx + \sum_{k=1}^{\infty}b_k\int_0^{2\pi}\sin(kx)\cos(nx)  \, dx$$

By orthogonality: First term $= 0$,  Second term: Only $k = n$ survives, giving $a_n \cdot \pi$,  Third term $= 0$ for all $k$

Therefore: $$\int_0^{2\pi} f(x)\cos(nx)  \, dx = a_n\pi$$,  $$a_n = \frac{1}{\pi}\int_0^{2\pi} f(x)\cos(nx)  \, dx$$

To find $b_n$, multiply both sides by $\sin(nx)$ and integrate: $$\int_0^{2\pi} f(x)\sin(nx)  \, dx = \sum_{k=1}^{\infty}a_k\int_0^{2\pi}\cos(kx)\sin(nx)  \, dx + \sum_{k=1}^{\infty}b_k\int_0^{2\pi}\sin(kx)\sin(nx)  \, dx$$

By orthogonality: First term $= 0$,  Second term: Only $k = n$ survives, giving $b_n \cdot \pi$

Therefore: $$\int_0^{2\pi} f(x)\sin(nx)  \, dx = b_n\pi$$,  $$b_n = \frac{1}{\pi}\int_0^{2\pi} f(x)\sin(nx)  \, dx$$

The orthogonality relations act like a "filter" that isolates each coefficient. This is analogous to finding components of a vector by taking dot products with basis vectors.

The Fourier series decomposes a function into "frequency components," with $a_k$ and $b_k$ representing the amplitudes of oscillations at frequency $k$.



### 6. Fourier Series Approach

To find sums like $\sum \frac{1}{n^2 + 1}$, we use Fourier series.

**Setup:** Consider the function $f(x) = e^{-x}$ on $[0, 2\pi)$, extended periodically.

**Fourier Series:** Any periodic function can be expressed as: $$f(x) = \frac{a_0}{2} + \sum_{k=1}^{\infty}\left(a_k\cos(kx) + b_k\sin(kx)\right)$$

where: $$a_k = \frac{1}{\pi}\int_0^{2\pi} f(x)\cos(kx)  \, dx, \quad b_k = \frac{1}{\pi}\int_0^{2\pi} f(x)\sin(kx)  \, dx$$

**Computing the coefficients for $f(x) = e^{-x}$:**

Using the integral formulas (derived from Euler's formula): 

$$\int e^{ax}\cos(bx)  \, dx = \frac{e^{ax}(a\cos(bx) + b\sin(bx))}{a^2 + b^2} + C$$

$$\int e^{ax}\sin(bx)  \, dx = \frac{e^{ax}(a\sin(bx) - b\cos(bx))}{a^2 + b^2} + C$$

For the constant term: $$a_0 = \frac{1}{\pi}\int_0^{2\pi} e^{-x}  \, dx = \frac{1}{\pi}[-e^{-x}]_0^{2\pi} = \frac{1-e^{-2\pi}}{\pi}$$

For $k \geq 1$: $$a_k = \frac{1}{\pi}\int_0^{2\pi} e^{-x}\cos(kx)  \, dx = \frac{1}{\pi} \cdot \frac{e^{-x}(-\cos(kx) + k\sin(kx))}{1+k^2}\Big|_0^{2\pi}$$

Since $\cos(2\pi k) = 1$ and $\sin(2\pi k) = 0$: $$= \frac{1}{\pi} \cdot \frac{-e^{-2\pi} + 1}{1+k^2} = \frac{1-e^{-2\pi}}{\pi(1+k^2)}$$

Similarly: $$b_k = \frac{1}{\pi} \cdot \frac{k(1-e^{-2\pi})}{1+k^2}$$

**Convergence at $x = 0$:** The Fourier series converges to the average of left and right limits: $$\frac{f(0^+) + f(0^-)}{2} = \frac{1 + e^{-2\pi}}{2}$$

**Substituting into the Fourier series at $x = 0$:**

$$\frac{1+e^{-2\pi}}{2} = \frac{1-e^{-2\pi}}{2\pi} + \sum_{k=1}^{\infty}\frac{1-e^{-2\pi}}{\pi(1+k^2)}$$

Simplify: $$\frac{1+e^{-2\pi}}{2} = \frac{1-e^{-2\pi}}{2\pi} + \frac{1-e^{-2\pi}}{\pi}\sum_{k=1}^{\infty}\frac{1}{1+k^2}$$

Solving for the sum: $$\sum_{k=1}^{\infty}\frac{1}{1+k^2} = \frac{\pi}{1-e^{-2\pi}} \cdot \left(\frac{1+e^{-2\pi}}{2} - \frac{1-e^{-2\pi}}{2\pi}\right)$$

After algebraic simplification:

**Theorem:** $$\boxed{\sum_{n=1}^{\infty}\frac{1}{n^2+1} = \frac{\pi}{2}\coth\pi - \frac{1}{2}}$$

where $\coth\pi = \frac{\cosh\pi}{\sinh\pi} = \frac{e^{\pi} + e^{-\pi}}{e^{\pi} - e^{-\pi}}$ is the hyperbolic cotangent.

Extension: by formally replacing $\pi$ with $it$ in the previous result, we obtain:

**Theorem:** $$\boxed{\sum_{n=1}^{\infty}\frac{1}{n^2-t^2} = \frac{1}{2t^2} - \frac{\pi\cot(\pi t)}{2t}}$$

