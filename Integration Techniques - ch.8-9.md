## Part IV: Rational and Algebraic Functions

有些助教感觉$\int \frac{dx}{x^5+1}$和$\int \frac{dx}{x^5}$味道应该差不多，你呢？

### 8. Partial Fractions

Partial fraction decomposition is the systematic method for integrating rational functions. It transforms a com rational expression into a sum of simpler fractions that can be integrated term by term.

------

### 8.1 Standard Decomposition

**Fundamental Principle:**

Any rational function $\frac{P(x)}{Q(x)}$ where $\deg(P) < \deg(Q)$ can be decomposed into partial fractions based on the factorization of $Q(x)$.

**(If $\deg(P) \geq \deg(Q)$, first perform polynomial long division.)**

**Decomposition Rules:**

1. **Linear factor $(x-a)$:** Contributes $\frac{A}{x-a}$
2. **Repeated linear factor $(x-a)^n$:** Contributes $\frac{A_1}{x-a} + \frac{A_2}{(x-a)^2} + \cdots + \frac{A_n}{(x-a)^n}$
3. **Irreducible quadratic $x^2+px+q$:** Contributes $\frac{Ax+B}{x^2+px+q}$
4. **Repeated irreducible quadratic $(x^2+px+q)^n$:** Contributes $\sum_{k=1}^n \frac{A_kx+B_k}{(x^2+px+q)^k}$

------

**Example 8.1.1:** $\int \frac{2x+1}{(x-1)(x+2)}dx$

Set up: $\frac{2x+1}{(x-1)(x+2)} = \frac{A}{x-1} + \frac{B}{x+2}$

Multiply through: $2x+1 = A(x+2) + B(x-1)$

- Set $x = 1$: $3 = 3A \Rightarrow A = 1$
- Set $x = -2$: $-3 = -3B \Rightarrow B = 1$

Therefore: $\int \left[\frac{1}{x-1} + \frac{1}{x+2}\right]dx = \ln|x-1| + \ln|x+2| + C = \ln|(x-1)(x+2)| + C$

------

### 8.2 Irreducible Quadratic Denominators

The strategy involves completing the square, substitution, and splitting the numerator.

**Strategy for $\int \frac{Ax+B}{(x^2+px+q)^n}dx$:**

**Step 1:** Complete the square in the denominator $$x^2+px+q = \left(x+\frac{p}{2}\right)^2 + \left(q-\frac{p^2}{4}\right)$$

Let $k^2 = q - \frac{p^2}{4}$ (assuming irreducible, so $k^2 > 0$)

**Step 2:** Substitute $u = x + \frac{p}{2}$, so $x = u - \frac{p}{2}$ and $dx = du$

The denominator becomes $(u^2 + k^2)^n$

**Step 3:** Express the numerator in terms of $u$: $$Ax + B = A\left(u - \frac{p}{2}\right) + B = Au + \left(B - \frac{Ap}{2}\right)$$

**Step 4:** Split into twointegrals: $$\int \frac{Au + (B - \frac{Ap}{2})}{(u^2+k^2)^n}du = A\int \frac{u}{(u^2+k^2)^n}du + \left(B - \frac{Ap}{2}\right)\int \frac{1}{(u^2+k^2)^n}du$$

**Step 5:** Evaluate each part:

- **First integral:** Let $w = u^2 + k^2$, $dw = 2u,du$ $$\int \frac{u}{(u^2+k^2)^n}du = \frac{1}{2}\int \frac{dw}{w^n} = \frac{1}{2} \cdot \frac{w^{-n+1}}{-n+1} + C = -\frac{1}{2(n-1)(u^2+k^2)^{n-1}} + C$$
- **Second integral:** Denote $I_n = \int \frac{du}{(u^2+k^2)^n}$
  - For $n = 1$: $I_1 = \frac{1}{k}\arctan\frac{u}{k} + C$
  - For $n \geq 2$: Use the **reduction formula** (derived below)

---

**Derivation of Reduction Formula for $I_n = \int \frac{du}{(u^2+k^2)^n}$:**

We begin with $I_{n-1} = \int \frac{du}{(u^2+k^2)^{n-1}}$ and use integration by parts:

Let $v = \frac{1}{(u^2+k^2)^{n-1}}$, then $dv = -\frac{2(n-1)u}{(u^2+k^2)^n}du$  
Let $dw = du$, then $w = u$

Applying integration by parts: $$I_{n-1} = \int v \, dw = vw - \int w \, dv$$  
$$= \frac{u}{(u^2+k^2)^{n-1}} - \int u \cdot \left(-\frac{2(n-1)u}{(u^2+k^2)^n}du\right)$$  
$$= \frac{u}{(u^2+k^2)^{n-1}} + 2(n-1)\int \frac{u^2}{(u^2+k^2)^n}du$$

Now rewrite $u^2 = (u^2+k^2) - k^2$:  
$$I_{n-1} = \frac{u}{(u^2+k^2)^{n-1}} + 2(n-1)\left[\int \frac{1}{(u^2+k^2)^{n-1}}du - k^2\int \frac{1}{(u^2+k^2)^n}du\right]$$  
$$= \frac{u}{(u^2+k^2)^{n-1}} + 2(n-1)(I_{n-1} - k^2 I_n)$$

Rearranging terms:  
$$I_{n-1} - 2(n-1)I_{n-1} = \frac{u}{(u^2+k^2)^{n-1}} - 2(n-1)k^2 I_n$$  
$$-(2n-3)I_{n-1} = \frac{u}{(u^2+k^2)^{n-1}} - 2(n-1)k^2 I_n$$  
$$2(n-1)k^2 I_n = \frac{u}{(u^2+k^2)^{n-1}} + (2n-3)I_{n-1}$$

Solving for $I_n$:  
$$\boxed{I_n = \frac{u}{2k^2(n-1)(u^2+k^2)^{n-1}} + \frac{2n-3}{2k^2(n-1)}I_{n-1}}$$

This reduction formula is valid for $n \geq 2$, with the base case:  
$$I_1 = \int \frac{du}{u^2+k^2} = \frac{1}{k}\arctan\frac{u}{k} + C$$

------

**Example 8.2.1:** Evaluate $\int \frac{x+1}{(x^2+4x+8)^2}dx$

**Solution:**

**Step 1: Complete the square** $$x^2 + 4x + 8 = (x+2)^2 + 4$$

So $k^2 = 4$, $k = 2$.

**Step 2: Substitute** $u = x+2$, so $x = u-2$, $dx = du$

$$\int \frac{x+1}{(x^2+4x+8)^2}dx = \int \frac{(u-2)+1}{(u^2+4)^2}du = \int \frac{u-1}{(u^2+4)^2}du$$

**Step 3: Split** $$= \int \frac{u}{(u^2+4)^2}du - \int \frac{1}{(u^2+4)^2}du$$

**Step 4: First integral**

Let $w = u^2+4$, $dw = 2u\,du$: $$\int \frac{u}{(u^2+4)^2}du = \frac{1}{2}\int \frac{dw}{w^2} = -\frac{1}{2w} + C = -\frac{1}{2(u^2+4)} + C$$

**Step 5: Second integral**

This is $I_2$ with $k = 2$. Use the reduction formula: $$I_2 = \frac{u}{2 \cdot 4 \cdot 1 \cdot (u^2+4)} + \frac{2(2)-3}{2 \cdot 4 \cdot 1}I_1$$

$$= \frac{u}{8(u^2+4)} + \frac{1}{8}I_1$$

$$I_1 = \frac{1}{2}\arctan\frac{u}{2}$$

$$I_2 = \frac{u}{8(u^2+4)} + \frac{1}{8} \cdot \frac{1}{2}\arctan\frac{u}{2}$$

$$= \frac{u}{8(u^2+4)} + \frac{\arctan(u/2)}{16}$$

**Step 6: Combine** $$= -\frac{1}{2(u^2+4)} - \left[\frac{u}{8(u^2+4)} + \frac{\arctan(u/2)}{16}\right] + C$$

$$= -\frac{1}{2(u^2+4)} - \frac{u}{8(u^2+4)} - \frac{\arctan(u/2)}{16} + C$$

$$= -\frac{4+u}{8(u^2+4)} - \frac{\arctan(u/2)}{16} + C$$

**Step 7: Back-substitute** $u = x+2$:

$$= -\frac{x+6}{8(x^2+4x+8)} - \frac{\arctan((x+2)/2)}{16} + C$$

------

**Example 8.2.2:** Evaluate $\int \frac{3x-2}{(x^2+2x+5)^2}dx$

**Solution:**

**Step 1:** Complete the square $$x^2+2x+5 = (x+1)^2 + 4$$

**Step 2:** Substitute $u = x+1$, so $x = u-1$: $$\int \frac{3(u-1)-2}{(u^2+4)^2}du = \int \frac{3u-5}{(u^2+4)^2}du$$

**Step 3:** Split: $$= 3\int \frac{u}{(u^2+4)^2}du - 5\int \frac{1}{(u^2+4)^2}du$$

**Step 4:** First integral: $$\int \frac{u}{(u^2+4)^2}du = -\frac{1}{2(u^2+4)}$$

**Step 5:** Second integral (from previous example): $$\int \frac{1}{(u^2+4)^2}du = \frac{u}{8(u^2+4)} + \frac{\arctan(u/2)}{16}$$

**Step 6:** Combine: $$= 3 \cdot \left(-\frac{1}{2(u^2+4)}\right) - 5\left[\frac{u}{8(u^2+4)} + \frac{\arctan(u/2)}{16}\right] + C$$

$$= -\frac{3}{2(u^2+4)} - \frac{5u}{8(u^2+4)} - \frac{5\arctan(u/2)}{16} + C$$

$$= -\frac{12 + 5u}{8(u^2+4)} - \frac{5\arctan(u/2)}{16} + C$$

**Step 7:** Back-substitute $u = x+1$:

$$= -\frac{12 + 5(x+1)}{8((x+1)^2+4)} - \frac{5\arctan((x+1)/2)}{16} + C$$

$$= -\frac{5x+17}{8(x^2+2x+5)} - \frac{5\arctan((x+1)/2)}{16} + C$$

------

**Example 8.2.3:** Evaluate $\int \frac{x^2+1}{x^2+4x+5}dx$

**Solution:**

The degree of numerator equals the degree of denominator, so perform polynomial division first.

Divide $x^2+1$ by $x^2+4x+5$: $$\frac{x^2+1}{x^2+4x+5} = 1 + \frac{-(4x+4)}{x^2+4x+5} = 1 - \frac{4x+4}{x^2+4x+5} = 1 - \frac{4(x+1)}{x^2+4x+5}$$

Therefore: $$\int \frac{x^2+1}{x^2+4x+5}dx = \int dx - 4\int \frac{x+1}{x^2+4x+5}dx$$

$$= x - 4\int \frac{x+1}{x^2+4x+5}dx$$

For the second integral, complete the square: $x^2+4x+5 = (x+2)^2 + 1$

Let $u = x+2$, so $x = u-2$ and $x+1 = u-1$: $$\int \frac{x+1}{x^2+4x+5}dx = \int \frac{u-1}{u^2+1}du$$

$$= \int \frac{u}{u^2+1}du - \int \frac{1}{u^2+1}du$$

$$= \frac{\ln(u^2+1)}{2} - \arctan(u) + C$$

$$= \frac{\ln(x^2+4x+5)}{2} - \arctan(x+2) + C$$

Therefore: $$\int \frac{x^2+1}{x^2+4x+5}dx = x - 4\left[\frac{\ln(x^2+4x+5)}{2} - \arctan(x+2)\right] + C$$

$$= x - 2\ln(x^2+4x+5) + 4\arctan(x+2) + C$$

------

### 8.3 High-Degree Polynomial Factorization

When dealing with denominators like $x^n \pm 1$, we can use roots of unity to factor them into real quadratic factors (and possibly linear factors).

**Roots of Unity**

The $n$-th roots of unity are solutions to $z^n = 1$: $$z_k = e^{2\pi ik/n} = \cos\frac{2\pi k}{n} + i\sin\frac{2\pi k}{n}, \quad k = 0, 1, ..., n-1$$

Similarly, for $z^n = -1$: $$z_k = e^{i\pi(2k+1)/n}, \quad k = 0, 1, ..., n-1$$

**Method 1:** Complex roots come in conjugate pairs, and each pair gives a real quadratic factor:

If $z = e^{i\theta}$ is a root, then so is $\bar{z} = e^{-i\theta}$, and: $$(x - e^{i\theta})(x - e^{-i\theta}) = x^2 - (e^{i\theta} + e^{-i\theta})x + e^{i\theta}e^{-i\theta}$$ $$= x^2 - 2\cos\theta \cdot x + 1$$

**Fundamental Theorem of Algebra:** Every polynomial of degree $n$ has exactly $n$ complex roots (counting multiplicity).

**Method 2 (See 8.4):** Complex Decomposition

1. Factor $Q(x)$ into complex linear factors
2. Write partial fractions with complex coefficients
3. Integrate to obtain complex logarithms
4. Combine conjugate terms to recover real-valued expressions

------

**Example 8.3.1:** Evaluate $\int \frac{dx}{x^4+1}$

**Step 1: Factorization:** $$x^4 + 1 = (x^2 - \sqrt{2}x + 1)(x^2 + \sqrt{2}x + 1)$$

**Step 2: Partial fraction decomposition**

$$\frac{1}{x^4+1} = \frac{Ax+B}{x^2-\sqrt{2}x+1} + \frac{Cx+D}{x^2+\sqrt{2}x+1}$$

$$1 = (Ax+B)(x^2+\sqrt{2}x+1) + (Cx+D)(x^2-\sqrt{2}x+1)$$

Comparing coefficients:

- Coefficient of $x^3$: $0 = A + C$, so $C = -A$
- Coefficient of $x^2$: $0 = \sqrt{2}A + B - \sqrt{2}C + D = 2\sqrt{2}A + B + D$
- Coefficient of $x^1$: $0 = A + \sqrt{2}B - C - \sqrt{2}D = 2A + \sqrt{2}(B-D)$
- Coefficient of $x^0$: $1 = B + D$

Solving the system gives:
$A = -\frac{\sqrt{2}}{4}$, $B = \frac{1}{2}$, $C = \frac{\sqrt{2}}{4}$, $D = \frac{1}{2}$

$$\frac{1}{x^4+1} = \frac{-\frac{\sqrt{2}}{4}x + \frac{1}{2}}{x^2-\sqrt{2}x+1} + \frac{\frac{\sqrt{2}}{4}x + \frac{1}{2}}{x^2+\sqrt{2}x+1}$$

**Step 3: Integrate**

For the first integral: $$x^2 - \sqrt{2}x + 1 = \left(x - \frac{\sqrt{2}}{2}\right)^2 + \frac{1}{2}$$

Let $u = x - \frac{\sqrt{2}}{2}$: $$\int \frac{-\frac{\sqrt{2}}{4}x + \frac{1}{2}}{x^2-\sqrt{2}x+1}dx = \int \frac{-\frac{\sqrt{2}}{4}(u+\frac{\sqrt{2}}{2}) + \frac{1}{2}}{u^2+\frac{1}{2}}du$$

$$= \int \frac{-\frac{\sqrt{2}}{4}u - \frac{1}{4} + \frac{1}{2}}{u^2+\frac{1}{2}}du = \int \frac{-\frac{\sqrt{2}}{4}u + \frac{1}{4}}{u^2+\frac{1}{2}}du$$

$$= -\frac{\sqrt{2}}{4}\int \frac{u}{u^2+\frac{1}{2}}du + \frac{1}{4}\int \frac{1}{u^2+\frac{1}{2}}du$$

$$= -\frac{\sqrt{2}}{8}\ln(u^2+\frac{1}{2}) + \frac{1}{4} \cdot \sqrt{2}\arctan(\sqrt{2}u) + C$$

$$= -\frac{\sqrt{2}}{8}\ln(x^2-\sqrt{2}x+1) + \frac{\sqrt{2}}{4}\arctan(\sqrt{2}x-1) + C$$

By similar analysis for the second integral: $$\int \frac{\frac{\sqrt{2}}{4}x + \frac{1}{2}}{x^2+\sqrt{2}x+1}dx = \frac{\sqrt{2}}{8}\ln(x^2+\sqrt{2}x+1) + \frac{\sqrt{2}}{4}\arctan(\sqrt{2}x+1) + C$$

**Answer:** $$\boxed{\frac{\sqrt{2}}{8}\ln\left|\frac{x^2+\sqrt{2}x+1}{x^2-\sqrt{2}x+1}\right| + \frac{\sqrt{2}}{4}[\arctan(\sqrt{2}x+1) + \arctan(\sqrt{2}x-1)] + C}$$

------

**Example 8.3.2:** Evaluate $\int \frac{dx}{x^5+1}$ (Only for illustration!)

**Step 1: Factor $x^5+1$**

The roots of $x^5 = -1$ are $z_k = e^{i\pi(2k+1)/5}$ for $k=0, 1, 2, 3, 4$. The angles are $\pi/5, 3\pi/5, \pi, 7\pi/5, 9\pi/5$.

The real factor is $(x+1)$ from $z_2 = e^{i\pi}=-1$.

Coupling symmetric angles:

$$x^{5}+1 = (x+1)\underbrace{(x^{2}-2x\cos(\pi/5)+1)}_{Q_1(x)}\underbrace{(x^{2}-2x\cos(3\pi/5)+1)}_{Q_2(x)}$$

where $\cos(\pi/5) = \frac{1+\sqrt{5}}{4}$ and $\cos(3\pi/5) = \frac{1-\sqrt{5}}{4}$.

**Step 2: Partial Fraction Decomposition (PFD)**

The decomposition is $\frac{1}{x^{5}+1} = \frac{A}{x+1} + \frac{B_{1}x+C_{1}}{Q_{1}(x)} + \frac{B_{2}x+C_{2}}{Q_{2}(x)}$.

Coefficients comparison is applicable, but here we will adopt a method that can be derived from Taylor expansion: the residue method.

$$A = \left.\frac{1}{(x^{5}+1)'}\right|_{x=-1} = \left.\frac{1}{5x^4}\right|_{x=-1} = \frac{1}{5}$$

Coefficients comparison gives $B_{1}, C_{1}, B_{2}, C_{2}$.

**Step 3: Integration and Final Answer**

The general solution structure for $I = \int\frac{dx}{x^{5}+1}$ is:

$$\int \frac{B_{k}x+C_{k}}{x^{2}-2x\cos\theta+1}dx = \frac{B_{k}}{2}\ln(x^{2}-2x\cos\theta+1) + \frac{B_{k}\cos\theta+C_{k}}{\sin\theta}\arctan\left(\frac{x-\cos\theta}{\sin\theta}\right)$$

$$\boxed{\int\frac{dx}{x^{5}+1} = \frac{1}{5}\ln|x+1|}$$
$$\boxed{ + \sum_{k=1}^2 \left[\frac{B_{k}}{2}\ln(x^{2}-2x\cos\theta_{k}+1) + \frac{B_{k}\cos\theta_{k}+C_{k}}{\sin\theta_{k}}\arctan\left(\frac{x-\cos\theta_{k}}{\sin\theta_{k}}\right)\right] + C}$$
where $\theta_1=\pi/5$, $\theta_2=3\pi/5$, and $B_k, C_k$ are the PFD coefficients.

------

**Example 8.3.3:** Evaluate $\int \frac{dx}{x^8+1}$ (Only for illustration!)

**Step 1: Factor $x^8+1$**

The roots of $x^8 = -1$ are $z_k = e^{i\pi(2k+1)/8}$ for $k = 0,1,...,7$.

Since $n=8$ is even and the power is $x^n+1$, there are no real roots. The roots form **four conjugate pairs** with angles $\theta_k = \frac{\pi}{8}, \frac{3\pi}{8}, \frac{5\pi}{8}, \frac{7\pi}{8}$.

$$x^8+1 = \prod_{k=0}^{3} \left(x^2 - 2x\cos\left(\frac{(2k+1)\pi}{8}\right) + 1\right)$$
$$ = (x^2 - 2x\cos(\pi/8) + 1)(x^2 - 2x\cos(3\pi/8) + 1)$$
$$\cdot (x^2 - 2x\cos(5\pi/8) + 1)(x^2 - 2x\cos(7\pi/8) + 1)$$

**Step 2: Partial Fraction Decomposition and Integration**

The PFD is $\frac{1}{x^8+1} = \sum_{k=1}^4 \frac{A_kx+B_k}{Q_k(x)}$. The final integral is a sum of four complex quadratic integrals.

**Final Answer:**

$$\boxed{\int \frac{dx}{x^8+1} = \sum_{k=1}^4 \left[\frac{A_{k}}{2}\ln(Q_{k}(x)) + \frac{A_{k}\cos\theta_{k}+B_{k}}{\sin\theta_{k}}\arctan\left(\frac{x-\cos\theta_{k}}{\sin\theta_{k}}\right)\right] + C}$$

where $Q_k(x) = x^2 - 2x\cos\theta_k + 1$, $\theta_k \in \{\pi/8, 3\pi/8, 5\pi/8, 7\pi/8\}$, and $A_k, B_k$ are the PFD coefficients determined by routine algebra.

------

**Example 8.3.4:** Evaluate $\int \frac{dx}{x^6-1}$

**Step 1: Factor $x^6-1$**

$$x^6 - 1 = (x^3-1)(x^3+1) = (x-1)(x^2+x+1)(x+1)(x^2-x+1)$$

**Step 2: Partial Fraction Decomposition (PFD)**

$$\frac{1}{x^6-1} = \frac{A}{x-1} + \frac{B}{x+1} + \frac{Cx+D}{x^2+x+1} + \frac{Ex+F}{x^2-x+1}$$

**A. Linear Term Coefficients:** 
- Set $x = 1$: $A(2)(3)(1) = 1 \Rightarrow A = \frac{1}{6}$
- Set $x = -1$: $B(-2)(1)(3) = 1 \Rightarrow B = -\frac{1}{6}$

**B. Quadratic Term Coefficients (Full PFD):**

$$\frac{1}{x^6-1} = \frac{1/6}{x-1} - \frac{1/6}{x+1} - \frac{(x+2)/6}{x^2+x+1} + \frac{(x-2)/6}{x^2-x+1}$$

**Step 3: Integration**

$$I = \frac{1}{6}\int\left(\frac{1}{x-1} - \frac{1}{x+1}\right)dx - \frac{1}{6}\int\frac{x+2}{x^2+x+1}dx + \frac{1}{6}\int\frac{x-2}{x^2-x+1}dx$$

For $\int\frac{x+2}{x^2+x+1}dx$: Complete the square: $x^2+x+1 = (x+\frac{1}{2})^2 + \frac{3}{4}$

Split: $\frac{1}{2}\int\frac{2x+1}{x^2+x+1}dx + \frac{3}{2}\int\frac{1}{x^2+x+1}dx$

$$= \frac{1}{2}\ln(x^2+x+1) + \frac{3}{2} \cdot \frac{2}{\sqrt{3}}\arctan\left(\frac{2x+1}{\sqrt{3}}\right) + C$$

$$= \frac{1}{2}\ln(x^2+x+1) + \sqrt{3}\arctan\left(\frac{2x+1}{\sqrt{3}}\right) + C$$

For $\int\frac{x-2}{x^2-x+1}dx$: Complete the square: $x^2-x+1 = (x-\frac{1}{2})^2 + \frac{3}{4}$

Split: $\frac{1}{2}\int\frac{2x-1}{x^2-x+1}dx - \frac{3}{2}\int\frac{1}{x^2-x+1}dx$

$$= \frac{1}{2}\ln(x^2-x+1) - \sqrt{3}\arctan\left(\frac{2x-1}{\sqrt{3}}\right) + C$$

**Final Answer:**

$$\boxed{\int \frac{dx}{x^6-1} = \frac{1}{6}\ln\left|\frac{x-1}{x+1}\right| - \frac{1}{12}\ln(x^2+x+1) + \frac{1}{12}\ln(x^2-x+1)}$$
$$\boxed{ - \frac{\sqrt{3}}{6}\arctan\left(\frac{2x+1}{\sqrt{3}}\right) - \frac{\sqrt{3}}{6}\arctan\left(\frac{2x-1}{\sqrt{3}}\right) + C}$$

The exam problem answers will not be more complicated than this one.

------

**Example 8.3.5:** Evaluate $\int \frac{x^2dx}{x^4+1}$

**Solution:**

$$x^4+1 = (x^2-\sqrt{2}x+1)(x^2+\sqrt{2}x+1)$$

**Partial fractions:** $$\frac{x^2}{x^4+1} = \frac{Ax+B}{x^2-\sqrt{2}x+1} + \frac{Cx+D}{x^2+\sqrt{2}x+1}$$

Multiply through: $$x^2 = (Ax+B)(x^2+\sqrt{2}x+1) + (Cx+D)(x^2-\sqrt{2}x+1)$$

By symmetry and coefficient matching:

- $x^3$: $0 = A + C$
- $x^2$: $1 = \sqrt{2}A + B - \sqrt{2}C + D$
- $x^1$: $0 = A + \sqrt{2}B - C - \sqrt{2}D$
- $x^0$: $0 = B + D$

Solving gives: $A = \frac{\sqrt{2}}{4}$, $B = 0$, $C = -\frac{\sqrt{2}}{4}$, $D = 0$

$$\frac{x^2}{x^4+1} = \frac{\frac{\sqrt{2}}{4}x}{x^2-\sqrt{2}x+1} + \frac{-\frac{\sqrt{2}}{4}x}{x^2+\sqrt{2}x+1}$$

**Integrate each term:**

For $\int \frac{\frac{\sqrt{2}}{4}x}{x^2-\sqrt{2}x+1}dx$:

Complete the square: $x^2 - \sqrt{2}x + 1 = (x - \frac{\sqrt{2}}{2})^2 + \frac{1}{2}$

$$= \frac{\sqrt{2}}{4}\int\frac{x}{x^2-\sqrt{2}x+1}dx$$

Let $u = x - \frac{\sqrt{2}}{2}$: $$= \frac{\sqrt{2}}{4}\int\frac{u+\frac{\sqrt{2}}{2}}{u^2+\frac{1}{2}}du$$

$$= \frac{\sqrt{2}}{4}\int\frac{u}{u^2+\frac{1}{2}}du + \frac{\sqrt{2}}{4}\cdot\frac{\sqrt{2}}{2}\int\frac{1}{u^2+\frac{1}{2}}du$$

$$= \frac{\sqrt{2}}{8}\ln(u^2+\frac{1}{2}) + \frac{1}{4}\cdot\sqrt{2}\arctan(\sqrt{2}u) + C$$

$$= \frac{\sqrt{2}}{8}\ln(x^2-\sqrt{2}x+1) + \frac{\sqrt{2}}{4}\arctan(\sqrt{2}x-1) + C$$

Similarly for $\int \frac{-\frac{\sqrt{2}}{4}x}{x^2+\sqrt{2}x+1}dx$: $$= -\frac{\sqrt{2}}{8}\ln(x^2+\sqrt{2}x+1) + \frac{\sqrt{2}}{4}\arctan(\sqrt{2}x+1) + C$$

**Combine:** $$\int \frac{x^2dx}{x^4+1} = \frac{\sqrt{2}}{8}\ln\left|\frac{x^2-\sqrt{2}x+1}{x^2+\sqrt{2}x+1}\right| + \frac{\sqrt{2}}{4}[\arctan(\sqrt{2}x-1) + \arctan(\sqrt{2}x+1)] + C$$

**Answer:** $$\boxed{\frac{\sqrt{2}}{8}\ln\left|\frac{x^2-\sqrt{2}x+1}{x^2+\sqrt{2}x+1}\right| + \frac{\sqrt{2}}{4}[\arctan(\sqrt{2}x-1) + \arctan(\sqrt{2}x+1)] + C}$$

---

**Example 8.3.6:** Evaluate $\int \sqrt{\tan x} \, dx$ 

(MATH1560J 2021 Second Midterm Examination, Exercise 2)

**Step 1: Substitution to Rationalize.**
Let $t = \sqrt{\tan x}$.

Then $t^2 = \tan x$, and $2t\,dt = \sec^2 x\ \, dx$.

Since $\sec^2 x = 1+\tan^2 x = 1+t^4$, we have $dx = \frac{2t}{1+t^4}\,dt$.

The integral becomes a rational function in $t$:

$$\int\sqrt{\tan x}\ \, dx = \int t \cdot \frac{2t}{1+t^4}\,dt = \int\mathbf{\frac{2t^{2}}{t^{4}+1}\,dt}$$

**Step 2: Integration of $\frac{2t^2}{t^4+1}$**

Using the PFD, integrating, and combining the resulting logarithmic and arctangent terms:

$$\int \frac{2t^2}{t^4+1}dt = \frac{1}{2\sqrt{2}}\ln\left(\frac{t^2-\sqrt{2}t+1}{t^2+\sqrt{2}t+1}\right) + \frac{1}{\sqrt{2}}\arctan\left(\frac{t^2-1}{\sqrt{2}t}\right) + C$$

**Step 3: Back Substitution ($t = \sqrt{\tan x}$)**

**Final Answer:**

$$\boxed{\int \sqrt{\tan x}\ \, dx = \frac{1}{2\sqrt{2}}\ln\left(\frac{\tan x-\sqrt{2\tan x}+1}{\tan x+\sqrt{2\tan x}+1}\right) + \frac{1}{\sqrt{2}}\arctan\left(\frac{\tan x-1}{\sqrt{2\tan x}}\right) + C}$$

Note that 8.3.5 and 8.3.6 have the same algebraic expression, but the answer differs in the tangent argument. This is because the substitution $t = \sqrt{\tan x}$ only maps $x \in (0, \frac{\pi}{2})$ to $t \in (0, +\infty)$, and the arctangent function has a period of $\pi$. Therefore, the two answers differ by a constant. 

Differing by a constant is a common occurrence when dealing with inverse trigonometric functions, as is also seen in the integration of $\sec x$ and $\csc x$, $arcsin x$ and $arccos x$, etc. Besides, trigonometric identities, such as double angle formulas or $\tan(x + \frac{\pi}{4}) = \frac{\tan x + 1}{1 - \tan x}$, can also lead to different forms. In the examinations, TAs will try as many forms as possible to check for equivalence. You will get full marks as long as you can justify the equivalence.


### 8.4 Complex Partial Fraction Decomposition

We can extend partial fraction decomposition to the complex domain by factoring polynomials into linear factors over $\mathbb{C}$. This approach often simplifies the integration process for high-degree polynomials.

Complex Analysis and Residue Calculus will be covered in MATH2560J, so don’t be worried if you struggle to understand this method.

**Fundamental Theorem of Algebra:** Every polynomial of degree $n$ has exactly $n$ complex roots (counting multiplicity).

**Theorem (Residue Formula for Partial Fractions):**
Let $Q(x)$ be a polynomial of degree $n$ with distinct roots $\alpha_1, \alpha_2, \ldots, \alpha_n$. Then for any polynomial $P(x)$ with $\deg(P) < n$, we have:

$$\frac{P(x)}{Q(x)} = \sum_{k=1}^n \frac{A_k}{x - \alpha_k}$$

where the coefficients are given by the residue formula:

$$\boxed{A_k = \frac{P(\alpha_k)}{Q'(\alpha_k)}}$$

**Proof:**

Let $Q(x) = c(x - \alpha_1)(x - \alpha_2)\cdots(x - \alpha_n)$ where $c$ is the leading coefficient.

**Step 1: Consider the function**
$$R(x) = \frac{P(x)}{Q(x)} - \sum_{k=1}^n \frac{A_k}{x - \alpha_k}$$

We want to choose $A_k$ such that $R(x) \equiv 0$.

**Step 2: Multiply both sides by $Q(x)$:**
$$P(x) - \sum_{k=1}^n A_k \cdot \frac{Q(x)}{x - \alpha_k} = Q(x)R(x)$$

**Step 3: Evaluate at $x = \alpha_j$:**
For $k \neq j$:
$$\lim_{x \to \alpha_j} \frac{Q(x)}{x - \alpha_k} = \frac{Q(\alpha_j)}{\alpha_j - \alpha_k} = 0$$

For $k = j$, we have the indeterminate form $\frac{0}{0}$. Using L'Hôpital's rule:
$$\lim_{x \to \alpha_j} \frac{Q(x)}{x - \alpha_j} = Q'(\alpha_j)$$

Therefore, evaluating at $x = \alpha_j$ gives:
$$P(\alpha_j) - A_j Q'(\alpha_j) = Q(\alpha_j)R(\alpha_j) = 0$$

**Step 4: Solve for $A_j$:**
$$A_j = \frac{P(\alpha_j)}{Q'(\alpha_j)}$$

**Step 5: Verify completeness:**
Both sides of the original equation are rational functions with the same poles and the same principal parts at each pole. Therefore, their difference is an entire rational function. Since $\deg(P) < n$ and the partial fraction sum has degree $< 0$, the difference is a polynomial of negative degree, hence identically zero.

**Corollary:** For the special case $P(x) = 1$, we have:
$$A_k = \frac{1}{Q'(\alpha_k)}$$

**Example Application:**
For $Q(x) = x^4 + 1$ with roots $\alpha_k = e^{i\pi(2k+1)/4}$, we have:
$$Q'(x) = 4x^3 \Rightarrow A_k = \frac{1}{4\alpha_k^3}$$

This is exactly the formula used in our complex partial fraction decompositions.

---

**Key Insight 1: Logarithm Sum $\Rightarrow$ Real Logarithm**
For a complex conjugate pair $\alpha$ and $\bar{\alpha}$, and real $x$:

$$\ln(x - \alpha) + \ln(x - \bar{\alpha}) = \ln(x - \alpha)(x - \bar{\alpha})$$

Let $\alpha = a + bi$, then:
$$(x - \alpha)(x - \bar{\alpha}) = (x - a - bi)(x - a + bi) = (x - a)^2 + b^2$$

Therefore:
$$\ln(x - \alpha) + \ln(x - \bar{\alpha}) = \ln(x - a)^2 + b^2$$

This is the mechanism by which complex logarithms combine to yield real logarithms of quadratic factors.

**Key Insight 2: Logarithm Difference $\Rightarrow$ Arctangent**
For the same conjugate pair:

$$\ln(x - \alpha) - \ln(x - \bar{\alpha}) = \ln\left(\frac{x - \alpha}{x - \bar{\alpha}}\right)$$

Let's analyze the argument:
$$\frac{x - \alpha}{x - \bar{\alpha}} = \frac{x - a - bi}{x - a + bi} = \frac{(x - a - bi)^2}{(x - a)^2 + b^2}$$

The magnitude is 1, so we're dealing purely with phase. Writing in polar form:
$$\frac{x - \alpha}{x - \bar{\alpha}} = e^{2i\theta} \quad \text{where} \quad \theta = -\arg(x - \alpha)$$

But more usefully, note that:
$$\frac{x - \alpha}{x - \bar{\alpha}} = \frac{(x - a) - bi}{(x - a) + bi}$$

This is a complex number on the unit circle. Its argument is:
$$\arg\left(\frac{x - \alpha}{x - \bar{\alpha}}\right) = -2\arctan\left(\frac{b}{x - a}\right)$$

Therefore:
$$\frac{1}{2i}[\ln(x - \alpha) - \ln(x - \bar{\alpha})] = \frac{1}{2i}\ln\left(\frac{x - \alpha}{x - \bar{\alpha}}\right) = \arctan\left(\frac{b}{x - a}\right)$$

This is the mechanism by which differences of complex logarithms yield arctangent terms.

**General Combination Formula:**
For complex coefficients $A$ and $\bar{A}$, and conjugate roots $\alpha$ and $\bar{\alpha}$:

$$A\ln(x - \alpha) + \bar{A}\ln(x - \bar{\alpha}) = 2\Re(A)\ln|x - \alpha| + 2\Im(A)\arg(x - \alpha)$$

Since $|x - \alpha|^2 = (x - a)^2 + b^2$ and $\arg(x - \alpha) = -\arctan\left(\frac{b}{x - a}\right)$, this becomes:

$$= \Re(A)\ln[(x - a)^2 + b^2] - 2\Im(A)\arctan\left(\frac{b}{x - a}\right)$$

This is the fundamental identity that allows us to recover real-valued expressions from complex partial fraction decompositions.

**Complex Decomposition Strategy:**

1. Factor $Q(x)$ into complex linear factors
2. Write partial fractions with complex coefficients using the residue theorem
3. Integrate to obtain complex logarithms
4. Combine conjugate terms using the above identities to recover real-valued expressions

---

**Example 8.4.1:** Evaluate $\int \frac{dx}{x^4+1}$ using complex methods

**Step 1: Complex Factorization**

Find all complex roots of $x^4 = -1$:
$$x^4 = -1 = e^{i(\pi + 2\pi k)} \Rightarrow x_k = e^{i\pi(2k+1)/4}, \quad k=0,1,2,3$$

- $x_0 = e^{i\pi/4} = \frac{\sqrt{2}}{2} + i\frac{\sqrt{2}}{2}$
- $x_1 = e^{i3\pi/4} = -\frac{\sqrt{2}}{2} + i\frac{\sqrt{2}}{2}$
- $x_2 = e^{i5\pi/4} = -\frac{\sqrt{2}}{2} - i\frac{\sqrt{2}}{2}$
- $x_3 = e^{i7\pi/4} = \frac{\sqrt{2}}{2} - i\frac{\sqrt{2}}{2}$

$$x^4+1 = (x-x_0)(x-x_1)(x-x_2)(x-x_3)$$

**Step 2: Complex Partial Fractions**

$$\frac{1}{x^4+1} = \frac{A}{x-x_0} + \frac{B}{x-x_1} + \frac{C}{x-x_2} + \frac{D}{x-x_3}$$

Using the residue formula: $A = \frac{1}{Q'(x_0)} = \frac{1}{4x_0^3}$

Calculate each coefficient:

- $A = \frac{1}{4e^{i3\pi/4}} = \frac{1}{4}e^{-i3\pi/4} = -\frac{\sqrt{2}}{8} - i\frac{\sqrt{2}}{8}$
- $B = \frac{1}{4e^{i9\pi/4}} = \frac{1}{4}e^{-i9\pi/4} = \frac{1}{4}e^{-i\pi/4} = \frac{\sqrt{2}}{8} - i\frac{\sqrt{2}}{8}$
- $C = \bar{B} = \frac{\sqrt{2}}{8} + i\frac{\sqrt{2}}{8}$
- $D = \bar{A} = -\frac{\sqrt{2}}{8} + i\frac{\sqrt{2}}{8}$

**Step 3: Integration**

$$\int \frac{dx}{x^4+1} = A\ln(x-x_0) + B\ln(x-x_1) + C\ln(x-x_2) + D\ln(x-x_3) + K$$

**Step 4: Combine Conjugate Terms**

Group conjugate pairs: $(A,D)$ and $(B,C)$

**First pair (A and D):**
$$A\ln(x-x_0) + D\ln(x-x_3) = A\ln(x-x_0) + \bar{A}\ln(x-\bar{x_0})$$

Using the identity:
$$A\ln(x-x_0) + \bar{A}\ln(x-\bar{x_0}) = 2\Re(A)\ln|x-x_0| + 2\Im(A)\arg(x-x_0)$$

Since $\Re(A) = -\frac{\sqrt{2}}{8}$ and $\Im(A) = -\frac{\sqrt{2}}{8}$:

$$= -\frac{\sqrt{2}}{4}\ln|x-x_0| - \frac{\sqrt{2}}{4}\arg(x-x_0)$$

But $|x-x_0|^2 = x^2 - \sqrt{2}x + 1$ and $\arg(x-x_0) = -\arctan\left(\frac{\sqrt{2}/2}{x - \sqrt{2}/2}\right)$

**Second pair (B and C):**
$$B\ln(x-x_1) + C\ln(x-x_2) = B\ln(x-x_1) + \bar{B}\ln(x-\bar{x_1})$$

With $\Re(B) = \frac{\sqrt{2}}{8}$ and $\Im(B) = -\frac{\sqrt{2}}{8}$:

$$= \frac{\sqrt{2}}{4}\ln|x-x_1| - \frac{\sqrt{2}}{4}\arg(x-x_1)$$

Where $|x-x_1|^2 = x^2 + \sqrt{2}x + 1$ and $\arg(x-x_1) = -\arctan\left(\frac{\sqrt{2}/2}{x + \sqrt{2}/2}\right)$

**Step 5: Final Combination**

Combining all terms and simplifying the arctangent expressions:

$$\int \frac{dx}{x^4+1} = \frac{\sqrt{2}}{8}\ln\left|\frac{x^2+\sqrt{2}x+1}{x^2-\sqrt{2}x+1}\right| + \frac{\sqrt{2}}{4}[\arctan(\sqrt{2}x+1) + \arctan(\sqrt{2}x-1)] + C$$

---

**Example 8.4.2:** Evaluate $\int \frac{dx}{x^5+1}$ using complex methods

**Step 1: Complex Factorization**

The roots of $x^5 = -1$ are:
$$x_k = e^{i\pi(2k+1)/5}, \quad k=0,1,2,3,4$$

Explicit angles: $\frac{\pi}{5}, \frac{3\pi}{5}, \pi, \frac{7\pi}{5}, \frac{9\pi}{5}$

$$x^5+1 = (x+1)(x-e^{i\pi/5})(x-e^{-i\pi/5})(x-e^{i3\pi/5})(x-e^{-i3\pi/5})$$

**Step 2: Complex Partial Fractions**

$$\frac{1}{x^5+1} = \frac{A}{x+1} + \frac{B}{x-e^{i\pi/5}} + \frac{C}{x-e^{-i\pi/5}} + \frac{D}{x-e^{i3\pi/5}} + \frac{E}{x-e^{-i3\pi/5}}$$

Using residue formula:

- $A = \frac{1}{5(-1)^4} = \frac{1}{5}$
- $B = \frac{1}{5e^{i4\pi/5}} = \frac{1}{5}e^{-i4\pi/5}$
- $C = \bar{B} = \frac{1}{5}e^{i4\pi/5}$
- $D = \frac{1}{5e^{i12\pi/5}} = \frac{1}{5}e^{-i12\pi/5} = \frac{1}{5}e^{-i2\pi/5}$
- $E = \bar{D} = \frac{1}{5}e^{i2\pi/5}$

**Step 3: Integration**

$$\int \frac{dx}{x^5+1} = \frac{1}{5}\ln|x+1| + B\ln(x-e^{i\pi/5}) + C\ln(x-e^{-i\pi/5})$$
$$ + D\ln(x-e^{i3\pi/5}) + E\ln(x-e^{-i3\pi/5}) + K$$

**Step 4: Combine Conjugate Terms**

**First conjugate pair (B and C):**
Let $\theta_1 = \pi/5$, then:
$$B\ln(x-e^{i\theta_1}) + C\ln(x-e^{-i\theta_1}) = 2\Re(B)\ln|x-e^{i\theta_1}| + 2\Im(B)\arg(x-e^{i\theta_1})$$

Calculate real and imaginary parts:
$$\Re(B) = \frac{1}{5}\cos\left(-\frac{4\pi}{5}\right) = \frac{1}{5}\cos\left(\frac{4\pi}{5}\right) = -\frac{1}{5}\cos\left(\frac{\pi}{5}\right)$$
$$\Im(B) = \frac{1}{5}\sin\left(-\frac{4\pi}{5}\right) = -\frac{1}{5}\sin\left(\frac{4\pi}{5}\right) = -\frac{1}{5}\sin\left(\frac{\pi}{5}\right)$$

After simplification, this gives:
$$= -\frac{2}{5}\cos(\pi/5)\ln\sqrt{x^2 - 2x\cos(\pi/5) + 1} - \frac{2}{5}\sin(\pi/5)\arctan\left(\frac{\sin(\pi/5)}{x - \cos(\pi/5)}\right)$$

**Second conjugate pair (D and E):**
Let $\theta_2 = 3\pi/5$, similar calculation gives:
$$= -\frac{2}{5}\cos(3\pi/5)\ln\sqrt{x^2 - 2x\cos(3\pi/5) + 1} - \frac{2}{5}\sin(3\pi/5)\arctan\left(\frac{\sin(3\pi/5)}{x - \cos(3\pi/5)}\right)$$

**Step 5: Final Answer**

Combining all terms and simplifying coefficients:

$$\int\frac{dx}{x^{5}+1} = \frac{1}{5}\ln|x+1|$$
$$ + \sum_{k=1}^2 \left[\frac{B_{k}}{2}\ln(x^{2}-2x\cos\theta_{k}+1) + \frac{B_{k}\cos\theta_{k}+C_{k}}{\sin\theta_{k}}\arctan\left(\frac{x-\cos\theta_{k}}{\sin\theta_{k}}\right)\right] + C$$

where $\theta_1=\pi/5$, $\theta_2=3\pi/5$, and:

- $B_1 = -\frac{2}{5}\cos(\pi/5)$, $C_1 = -\frac{2}{5}\sin(\pi/5)$
- $B_2 = -\frac{2}{5}\cos(3\pi/5)$, $C_2 = -\frac{2}{5}\sin(3\pi/5)$

---

**Example 8.4.3:** Evaluate $\int \frac{dx}{x^6-1}$ using complex methods

**Step 1: Complex Factorization**

The roots of $x^6 = 1$ are the 6th roots of unity:
$$x_k = e^{2\pi ik/6} = e^{\pi ik/3}, \quad k=0,1,2,3,4,5$$

- $x_0 = 1$
- $x_1 = e^{i\pi/3} = \frac{1}{2} + i\frac{\sqrt{3}}{2}$
- $x_2 = e^{i2\pi/3} = -\frac{1}{2} + i\frac{\sqrt{3}}{2}$
- $x_3 = -1$
- $x_4 = e^{i4\pi/3} = -\frac{1}{2} - i\frac{\sqrt{3}}{2}$
- $x_5 = e^{i5\pi/3} = \frac{1}{2} - i\frac{\sqrt{3}}{2}$

$$x^6-1 = (x-1)(x+1)(x-e^{i\pi/3})(x-e^{-i\pi/3})(x-e^{i2\pi/3})(x-e^{-i2\pi/3})$$

**Step 2: Complex Partial Fractions**

$$\frac{1}{x^6-1} = \frac{A}{x-1} + \frac{B}{x+1} + \frac{C}{x-e^{i\pi/3}} + \frac{D}{x-e^{-i\pi/3}} + \frac{E}{x-e^{i2\pi/3}} + \frac{F}{x-e^{-i2\pi/3}}$$

Using residue formula:

- $A = \frac{1}{6(1)^5} = \frac{1}{6}$
- $B = \frac{1}{6(-1)^5} = -\frac{1}{6}$
- $C = \frac{1}{6e^{i5\pi/3}} = \frac{1}{6}e^{-i5\pi/3} = \frac{1}{6}e^{i\pi/3}$
- $D = \bar{C} = \frac{1}{6}e^{-i\pi/3}$
- $E = \frac{1}{6e^{i10\pi/3}} = \frac{1}{6}e^{-i10\pi/3} = \frac{1}{6}e^{i2\pi/3}$
- $F = \bar{E} = \frac{1}{6}e^{-i2\pi/3}$

**Step 3: Integration**

$$\int \frac{dx}{x^6-1} = \frac{1}{6}\ln|x-1| - \frac{1}{6}\ln|x+1| + C\ln(x-e^{i\pi/3})$$
$$ + D\ln(x-e^{-i\pi/3}) + E\ln(x-e^{i2\pi/3}) + F\ln(x-e^{-i2\pi/3}) + K$$

**Step 4: Combine Conjugate Terms**

**First conjugate pair (C and D):**
Let $\theta = \pi/3$, then:
$$C\ln(x-e^{i\theta}) + D\ln(x-e^{-i\theta}) = 2\Re(C)\ln|x-e^{i\theta}| + 2\Im(C)\arg(x-e^{i\theta})$$

Calculate:
$$\Re(C) = \frac{1}{6}\cos(\pi/3) = \frac{1}{12}$$
$$\Im(C) = \frac{1}{6}\sin(\pi/3) = \frac{\sqrt{3}}{12}$$

This gives:
$$= \frac{1}{6}\ln\sqrt{x^2 - x + 1} + \frac{\sqrt{3}}{6}\arctan\left(\frac{\sqrt{3}/2}{x - 1/2}\right)$$

**Second conjugate pair (E and F):**
Let $\phi = 2\pi/3$, then:
$$E\ln(x-e^{i\phi}) + F\ln(x-e^{-i\phi}) = 2\Re(E)\ln|x-e^{i\phi}| + 2\Im(E)\arg(x-e^{i\phi})$$

Calculate:
$$\Re(E) = \frac{1}{6}\cos(2\pi/3) = -\frac{1}{12}$$
$$\Im(E) = \frac{1}{6}\sin(2\pi/3) = \frac{\sqrt{3}}{12}$$

This gives:
$$= -\frac{1}{6}\ln\sqrt{x^2 + x + 1} + \frac{\sqrt{3}}{6}\arctan\left(\frac{\sqrt{3}/2}{x + 1/2}\right)$$

**Step 5: Final Combination**

Combining all terms and simplifying:

$$\int \frac{dx}{x^6-1} = \frac{1}{6}\ln\left|\frac{x-1}{x+1}\right| - \frac{1}{12}\ln(x^2+x+1) + \frac{1}{12}\ln(x^2-x+1)$$
$$- \frac{\sqrt{3}}{6}\arctan\left(\frac{2x+1}{\sqrt{3}}\right) - \frac{\sqrt{3}}{6}\arctan\left(\frac{2x-1}{\sqrt{3}}\right) + C$$

---

**Summary:** Complex partial fraction decomposition provides a systematic approach to integrating rational functions. The key insight is that complex logarithms from conjugate pairs combine to yield real logarithms and arctangent functions in the final answer.

---



## Part VI: Definite Integral

我心澎湃，式限合一。

### 9. Common Methods for Definite Integral

Some integrals, despite their simple appearance, cannot be expressed in terms of elementary functions (polynomials, exponentials, logarithms, trigonometric functions, and their inverses). However, we can still evaluate definite integrals involving these forms using clever techniques, and in the process, encounter important special functions that appear throughout mathematics and physics.

### 9.1 King Property (Substitution $x \to a+b-x$)

**Theorem:** For any integrable function $f$: $$\int_a^b f(x)dx = \int_a^b f(a+b-x)dx$$

**Proof:** Let $u = a+b-x$, then $du = -dx$. When $x=a$, $u=b$; when $x=b$, $u=a$: $$\int_a^b f(a+b-x)dx = -\int_b^a f(u)du = \int_a^b f(u)du = \int_a^b f(x)dx$$

**Application Strategy:**

1. Compute $I = \int_a^b f(x)dx$
2. Also write $I = \int_a^b f(a+b-x)dx$
3. Add both expressions: $2I = \int_a^b [f(x) + f(a+b-x)]dx$
4. The sum often simplifies dramatically

------

**Example 9.1.1:** Evaluate $\int_0^{\pi/2} \frac{\sin x}{\sin x + \cos x}dx$

**Solution:**

Let $I = \int_0^{\pi/2} \frac{\sin x}{\sin x + \cos x}dx$

Apply King property with $a=0$, $b=\pi/2$, so $a+b-x = \pi/2 - x$: $$I = \int_0^{\pi/2} \frac{\sin(\pi/2-x)}{\sin(\pi/2-x)+\cos(\pi/2-x)}dx$$

Using $\sin(\pi/2-x) = \cos x$ and $\cos(\pi/2-x) = \sin x$: $$I = \int_0^{\pi/2} \frac{\cos x}{\cos x + \sin x}dx$$

Add both expressions: $$2I = \int_0^{\pi/2} \frac{\sin x + \cos x}{\sin x + \cos x}dx = \int_0^{\pi/2} 1 \, dx = \frac{\pi}{2}$$

Therefore: $I = \frac{\pi}{4}$

------

**Example 9.1.2:** Evaluate $\int_0^\pi \frac{x\sin x}{1+\cos^2 x}dx$

**Solution:**

Let $I = \int_0^\pi \frac{x\sin x}{1+\cos^2 x}dx$

Apply King property with $a+b-x = \pi - x$: $$I = \int_0^\pi \frac{(\pi-x)\sin(\pi-x)}{1+\cos^2(\pi-x)}dx$$

Using $\sin(\pi-x) = \sin x$ and $\cos(\pi-x) = -\cos x$: $$I = \int_0^\pi \frac{(\pi-x)\sin x}{1+\cos^2 x}dx$$

Add both: $$2I = \int_0^\pi \frac{x\sin x + (\pi-x)\sin x}{1+\cos^2 x}dx = \int_0^\pi \frac{\pi\sin x}{1+\cos^2 x}dx$$

$$2I = \pi\int_0^\pi \frac{\sin x}{1+\cos^2 x}dx$$

Let $u = \cos x$, $du = -\sin x \, dx$. When $x=0$, $u=1$; when $x=\pi$, $u=-1$: $$2I = \pi\int_1^{-1} \frac{-du}{1+u^2} = \pi\int_{-1}^1 \frac{du}{1+u^2}$$

$$= \pi[\arctan(u)]_{-1}^1 = \pi\left[\frac{\pi}{4} - \left(-\frac{\pi}{4}\right)\right] = \pi \cdot \frac{\pi}{2} = \frac{\pi^2}{2}$$

Therefore: $I = \frac{\pi^2}{4}$

------

**Example 9.1.3:** Show that $\int_0^{\pi} xf(\sin x)dx = \frac{\pi}{2}\int_0^\pi f(\sin x)dx$

**Solution:**

Let $I = \int_0^\pi xf(\sin x)dx$

Apply King property with $\pi - x$: $$I = \int_0^\pi (\pi-x)f(\sin(\pi-x))dx = \int_0^\pi (\pi-x)f(\sin x)dx$$

(since $\sin(\pi-x) = \sin x$)

Add: $$2I = \int_0^\pi [x + (\pi-x)]f(\sin x)dx = \pi\int_0^\pi f(\sin x)dx$$

Therefore: $$\boxed{\int_0^\pi xf(\sin x)dx = \frac{\pi}{2}\int_0^\pi f(\sin x)dx}$$

**Application:** This is a powerful reduction formula for integrals of the form $\int_0^\pi xg(\sin x)dx$.

------

**Example 9.1.4:** Evaluate $\int_0^{2\pi} \frac{x\sin^2 x}{1+\cos x}dx$

**Solution:**

Use King property on $[0,2\pi]$ with $2\pi-x$:

Let $I = \int_0^{2\pi} \frac{x\sin^2 x}{1+\cos x}dx$

$$I = \int_0^{2\pi} \frac{(2\pi-x)\sin^2(2\pi-x)}{1+\cos(2\pi-x)}dx = \int_0^{2\pi} \frac{(2\pi-x)\sin^2 x}{1+\cos x}dx$$

Adding: $2I = 2\pi\int_0^{2\pi} \frac{\sin^2 x}{1+\cos x}dx$

Now evaluate $J = \int_0^{2\pi} \frac{\sin^2 x}{1+\cos x}dx = \int_0^{2\pi} \frac{1-\cos^2 x}{1+\cos x}dx$ 

$$= \int_0^{2\pi} \frac{(1-\cos x)(1+\cos x)}{1+\cos x}dx = \int_0^{2\pi} (1-\cos x)dx$$ $$= [x - \sin x]_0^{2\pi} = 2\pi$$

Therefore: $2I = 2\pi \cdot 2\pi = 4\pi^2$, so $I = 2\pi^2$

------

### 9.2 Even-Odd Function Properties

**Theorem:**

1. If $f(-x) = f(x)$ (even): $\int_{-a}^a f(x)dx = 2\int_0^a f(x)dx$
2. If $f(-x) = -f(x)$ (odd): $\int_{-a}^a f(x)dx = 0$

------

**Example 9.2.1:** Evaluate $\int_{-\pi}^\pi \frac{x^2\cos x}{1+e^x}dx$

Use the substitution $ u = -x $. Then $ du = -dx $, and when $ x = -\pi $, $ u = \pi $; when $ x = \pi $, $ u = -\pi $. Thus,

$$I = \int_{u=\pi}^{-\pi} \frac{(-u)^2 \cos(-u)}{1 + e^{-u}} (-du) = \int_{\pi}^{-\pi} \frac{u^2 \cos u}{1 + e^{-u}} (-du)$$

Reversing the limits of integration removes the minus sign:

$$I = \int_{-\pi}^{\pi} \frac{u^2 \cos u}{1 + e^{-u}}  du$$

Since the variable of integration is dummy, we may replace $ u $ with $ x $:

$$I = \int_{-\pi}^{\pi} \frac{x^2 \cos x}{1 + e^{-x}}  dx$$

Now add the original expression:

$$2I = \int_{-\pi}^{\pi} x^2 \cos x \left( \frac{1}{1 + e^x} + \frac{1}{1 + e^{-x}} \right) dx$$

Note that $$\frac{1}{1 + e^x} + \frac{1}{1 + e^{-x}} = \frac{1 + e^x}{1 + e^x} = 1$$, so $$2I_1 = \int_{-\pi}^{\pi} x^2 \cos x  dx$$.

Therefore, $$I = \int_{0}^{\pi} x^2 \cos x  dx$$

$$ = \left[ x^2 \sin x \right]_{0}^{\pi} - \int_{0}^{\pi} 2x \sin x  dx = 0 - 2 \int_{0}^{\pi} x \sin x  dx$$

$$ = -2\left[ -x \cos x \right]_{0}^{\pi} -2 \int_{0}^{\pi} \cos x  dx = -2(-\pi \cos \pi + 0) -2 \left[ \sin x \right]_{0}^{\pi} = \boxed{-2\pi} $$

------

### 9.3 Periodic Function Integrals

**Properties:**

1. If $f(x+T) = f(x)$, then $\int_0^{nT} f(x)dx = n\int_0^T f(x)dx$
2. **Shift property:** $\int_a^{a+T} f(x)dx = \int_0^T f(x)dx$

------

**Example 9.3.1:** Evaluate $\int_0^{3\pi} |\sin x|dx$

**Solution:**

The function $|\sin x|$ has period $\pi$ (not $2\pi$).

Therefore: $$\int_0^{3\pi} |\sin x|dx = 3\int_0^\pi |\sin x|dx$$

On $[0,\pi]$, $\sin x \geq 0$, so $|\sin x| = \sin x$: 

$$= 3\int_0^\pi \sin x \, dx = 3[-\cos x]_0^\pi = 3[-(-1) - (-1)] = 3 \cdot 2 = 6$$

------

**Example 9.3.2:** Evaluate $\int_5^{11} \cos^2(\pi x)dx$

**Solution:**

The function $\cos^2(\pi x)$ has period $T = 1$

(since $\cos^2(\pi(x+1)) = \cos^2(\pi x + \pi) = \cos^2(\pi x)$).

The interval $[5,11]$ has length $6 = 6T$, so: 

$$\int_5^{11} \cos^2(\pi x)dx = \int_0^6 \cos^2(\pi x)dx = 6\int_0^1 \cos^2(\pi x)dx$$

Now: $\cos^2(\pi x) = \frac{1+\cos(2\pi x)}{2}$

$$\int_0^1 \cos^2(\pi x)dx = \int_0^1 \frac{1+\cos(2\pi x)}{2}dx$$ $$= \frac{1}{2}\left[x + \frac{\sin(2\pi x)}{2\pi}\right]_0^1 = \frac{1}{2}[1 + 0 - 0 - 0] = \frac{1}{2}$$

Therefore: $\int_5^{11} \cos^2(\pi x)dx = 6 \cdot \frac{1}{2} = 3$

------

### 9.4 Wallis's Formula

For integrals of the form $I_n = \int_0^{\pi/2} \sin^n x \, dx$ or $\int_0^{\pi/2} \cos^n x \, dx$:

**Key observations:**

1. By substitution $u = \pi/2 - x$: $\int_0^{\pi/2} \sin^n x \, dx = \int_0^{\pi/2} \cos^n x \, dx$
2. Both satisfy the reduction formula: $I_n = \frac{n-1}{n}I_{n-2}$

**Wallis's Formula:** $$\int_0^{\pi/2} \sin^{2n} x \, dx = \int_0^{\pi/2} \cos^{2n} x \, dx = \frac{(2n-1)!!}{(2n)!!} \cdot \frac{\pi}{2}$$

$$\int_0^{\pi/2} \sin^{2n+1} x \, dx = \int_0^{\pi/2} \cos^{2n+1} x \, dx = \frac{(2n)!!}{(2n+1)!!}$$

where $n!! = n(n-2)(n-4)\cdots$ (double factorial).

**Connection:** The ratio $\frac{I_{2n}}{I_{2n+1}} \to 1$ as $n \to \infty$, which leads to Wallis's product: 

$$\frac{\pi}{2} = \prod_{n=1}^\infty \frac{(2n)(2n)}{(2n-1)(2n+1)} = \frac{2 \cdot 2}{1 \cdot 3} \cdot \frac{4 \cdot 4}{3 \cdot 5} \cdot \frac{6 \cdot 6}{5 \cdot 7} \cdots$$

------

### 9.5 Feynman's Trick for Evaluation

Feynman's trick involves introducing a parameter to make an integral easier, differentiating with respect to that parameter, solving the simpler problem, then integrating back.

Nevertheless, chances are that the extra parameter to introduce has multiple choices but only one (or even zero) agreeable solution. Therefore, this trick involves deeper considerations beyond the scope of elementary calculus, and the following examples are just for illustration.

------

**Example 9.5.1:** Evaluate $\int_0^1 \frac{x^2-1}{\ln x}dx$

**Solution:**

**Step 1: Introduce parameter**

Consider: $I(a) = \int_0^1 \frac{x^a-1}{\ln x}dx$. We want $I(2)$.

**Step 2: Differentiate**

$$I'(a) = \frac{d}{da}\int_0^1 \frac{x^a-1}{\ln x}dx = \int_0^1 \frac{\partial}{\partial a}\left(\frac{x^a-1}{\ln x}\right)dx$$

$$= \int_0^1 \frac{x^a \ln x}{\ln x}dx = \int_0^1 x^a \, dx = \left[\frac{x^{a+1}}{a+1}\right]_0^1 = \frac{1}{a+1}$$

**Step 3: Integrate back**

$$I(a) = \int \frac{1}{a+1}da = \ln(a+1) + C$$

**Step 4: Find constant**

At $a=0$: $I(0) = \int_0^1 \frac{1-1}{\ln x}dx = 0$

So: $0 = \ln(1) + C$, giving $C = 0$

Therefore: $I(a) = \ln(a+1)$. $I(2) = \ln(3)$

------

**Example 9.5.2:** Evaluate $\int_0^\infty \frac{e^{-ax} - e^{-bx}}{x}dx$ 

**Solution:**

**Step 1: Introduce parameter**

Consider: $I(a) = \int_0^\infty \frac{e^{-ax}}{x}dx$

We want: $I(a) - I(b) = \int_0^\infty \frac{e^{-ax} - e^{-bx}}{x}dx$

**Step 2: Differentiate**

$I'(a) = \frac{d}{da}\int_0^\infty \frac{e^{-ax}}{x}dx = \int_0^\infty \frac{\partial}{\partial a}\left(\frac{e^{-ax}}{x}\right)dx$

$= \int_0^\infty \frac{-xe^{-ax}}{x}dx = -\int_0^\infty e^{-ax}dx$

$= -\left[-\frac{e^{-ax}}{a}\right]_0^\infty = -\frac{1}{a}$

**Step 3: Integrate back**

$I(a) = -\int \frac{da}{a} = -\ln|a| + C$

**Step 4: Apply to difference**

$I(a) - I(b) = -\ln|a| + \ln|b| = \ln\left|\frac{b}{a}\right|$

For $a, b > 0$:

**Answer:** $\boxed{\ln\left(\frac{b}{a}\right)}$

------

### 9.6 Riemann Sum Limits

**Recognition:** Limits of the form: $\lim_{n\to\infty} \frac{1}{n}\sum_{k=1}^n f(k/n) = \int_0^1 f(x)dx$

**General form:** $\lim_{n\to\infty} \frac{b-a}{n}\sum_{k=1}^n f\left(a + k\frac{b-a}{n}\right) = \int_a^b f(x)dx$

------

**Example 9.6.1:** Evaluate $\lim_{n\to\infty} \frac{1}{n}\sum_{k=1}^n \sqrt{\frac{k}{n}}$

**Solution:** Recognize as: $\int_0^1 \sqrt{x} \, dx$ $ = \int_0^1 x^{1/2}dx = \left[\frac{x^{3/2}}{3/2}\right]_0^1 = \frac{2}{3}$

---

**Example 9.6.2:** Evaluate $\lim_{n\to\infty} \sum_{k=1}^n \ln(1+k/n)\cdot(1/n)$

**Solution:**

Recognize as a Riemann sum for $f(x) = \ln(1+x)$ on $[0,1]$:

$\lim_{n\to\infty} \frac{1}{n}\sum_{k=1}^n \ln(1+k/n) = \int_0^1 \ln(1+x)dx$

**Evaluate the integral** using integration by parts:

Let $u = \ln(1+x)$, $dv = dx$, so $du = \frac{dx}{1+x}$, $v = x$:

$\int_0^1 \ln(1+x)dx = [x\ln(1+x)]_0^1 - \int_0^1 \frac{x}{1+x}dx$

$= 1 \cdot \ln(2) - 0 - \int_0^1 \frac{x}{1+x}dx$

For the remaining integral, write: $\frac{x}{1+x} = \frac{(1+x)-1}{1+x} = 1 - \frac{1}{1+x}$

$\int_0^1 \frac{x}{1+x}dx = \int_0^1 \left(1 - \frac{1}{1+x}\right)dx = [x - \ln(1+x)]_0^1$

$= 1 - \ln(2) - 0 = 1 - \ln(2)$

Therefore: $= \ln(2) - (1 - \ln(2)) = 2\ln(2) - 1$

------

**Example 9.6.3:** Evaluate $\lim_{n\to\infty} \sum_{k=1}^n \frac{n}{n^2+k^2}$

**Solution:**

Rewrite: $\frac{n}{n^2+k^2} = \frac{1}{n} \cdot \frac{1}{1+(k/n)^2}$

Therefore: $\lim_{n\to\infty} \sum_{k=1}^n \frac{n}{n^2+k^2} = \lim_{n\to\infty} \sum_{k=1}^n \frac{1}{1+(k/n)^2} \cdot \frac{1}{n}$

$= \int_0^1 \frac{dx}{1+x^2} = [\arctan x]_0^1 = \frac{\pi}{4}$

------

**Example 9.6.4:** Evaluate $\lim_{n\to\infty} \frac{\pi}{n}\sum_{k=1}^n \sin(\frac{k\pi}{n})$

**Solution:**

This is a Riemann sum with $\Delta x = \frac{\pi}{n}$ on $[0,\pi]$:

$\lim_{n\to\infty} \frac{\pi}{n}\sum_{k=1}^n \sin\left(\frac{k\pi}{n}\right) = \int_0^\pi \sin x \, dx$

$= [-\cos x]_0^\pi = -(-1) - (-1) = 2$

---

**Example 9.6.5:**Evaluate $$\lim_{n \to \infty} \left( \frac{n!}{n^n} \right)^{1/n}$$

(MATH1560J 2021 Second Midterm Examination, Exercise 4)

**Solution:**

Let $L$ be the limit, then:
$$\ln L = \lim_{n \to \infty} \frac{1}{n} \ln\left( \frac{n!}{n^n} \right) = \lim_{n \to \infty} \frac{1}{n} \ln\left( \frac{1}{n} \cdot \frac{2}{n} \cdots \frac{n}{n} \right)$$
$$= \lim_{n \to \infty} \frac{1}{n} \sum_{k=1}^n \ln\left( \frac{k}{n} \right)$$

Recognize as a Riemann sum:
$$= \int_0^1 \ln x  dx = [x\ln x - x]_0^1 = -1$$

Therefore: $L = e^{-1}$

------

