# Functions Revisited in Complex (Revised)

Yuebo Hu, TA of MATH1560J, GC, SJTU

liuyejiang576@sjtu.edu.cn

October, 2025



> "In the arithmetic of the universe, complex numbers are the natural language, and real numbers are but a shadow."
>
> — **Leonhard Euler**



## Part I: Complex Numbers

## 1. Polar Form

Every complex number $z = x + iy$ can be written in **polar form**:

$$z = r(\cos\theta + i\sin\theta)$$

where:
- $r = |z| = \sqrt{x^2 + y^2}$ is the **modulus** (distance from origin)
- $\theta = \arg(z)$ is the **argument** (angle from positive real axis)

**Example:** Express $z = -\sqrt{3} + i$ in polar form.

**Solution:**
- $r = \sqrt{3 + 1} = 2$
- The point is in the second quadrant, so $\theta = \pi - \arctan(1/\sqrt{3}) = \pi - \pi/6 = 5\pi/6$
- Therefore: $-\sqrt{3} + i = 2(\cos\frac{5\pi}{6} + i\sin\frac{5\pi}{6})$



## 2. Fundamental Theorem

When multiplying complex numbers in polar form:

- **Moduli multiply**: $|z_1 z_2| = |z_1| \cdot |z_2|$
- **Arguments add**: $\arg(z_1 z_2) = \arg(z_1) + \arg(z_2)$

**Proof:**

Let $z_1 = r_1(\cos\theta_1 + i\sin\theta_1)$ and $z_2 = r_2(\cos\theta_2 + i\sin\theta_2)$.

$$\begin{align}
z_1 z_2 &= r_1 r_2(\cos\theta_1 + i\sin\theta_1)(\cos\theta_2 + i\sin\theta_2)\\
&= r_1 r_2[(\cos\theta_1\cos\theta_2 - \sin\theta_1\sin\theta_2) + i(\sin\theta_1\cos\theta_2 + \cos\theta_1\sin\theta_2)]
\end{align}$$

Recall the **angle addition formulas** from trigonometry:
- $\cos(\theta_1 + \theta_2) = \cos\theta_1\cos\theta_2 - \sin\theta_1\sin\theta_2$
- $\sin(\theta_1 + \theta_2) = \sin\theta_1\cos\theta_2 + \cos\theta_1\sin\theta_2$

Therefore:
$$z_1 z_2 = r_1 r_2[\cos(\theta_1 + \theta_2) + i\sin(\theta_1 + \theta_2)]$$

Multiplying by a complex number $w$ transforms every point $z$ by:
1. **Scaling** by a factor of $|w|$
2. **Rotating** counterclockwise by angle $\arg(w)$

**Special Case:** If $|w| = 1$, then $w$ represents a **pure rotation**.

Similarly, for division:
$$\frac{z_1}{z_2} = \frac{r_1}{r_2}[\cos(\theta_1 - \theta_2) + i\sin(\theta_1 - \theta_2)]$$

Moduli divide, arguments subtract.

**Example:** Compute $\frac{1+i}{-\sqrt{3}+i}$ using polar form.

**Solution:**
$$\frac{1+i}{-\sqrt{3}+i} = \frac{\sqrt{2}}{2}[\cos(\pi/4 - 5\pi/6) + i\sin(\pi/4 - 5\pi/6)] = \frac{\sqrt{2}}{2}[\cos(-7\pi/12) + i\sin(-7\pi/12)]$$



## 3. Power (De Moivre Theorem)

For any integer $n$:
$$(\cos\theta + i\sin\theta)^n = \cos(n\theta) + i\sin(n\theta)$$

**Proof by Induction:**

Base case ($n = 1$): Trivially true.

Inductive step: Assume true for $n = k$. Then:
$$\begin{align}
(\cos\theta + i\sin\theta)^{k+1} &= (\cos\theta + i\sin\theta)^k \cdot (\cos\theta + i\sin\theta)\\
&= [\cos(k\theta) + i\sin(k\theta)][\cos\theta + i\sin\theta]\\
&= \cos((k+1)\theta) + i\sin((k+1)\theta)
\end{align}$$

where the last step uses the multiplication formula.

**Remark:** This also works for negative integers by noting that 
$$(\cos\theta + i\sin\theta)^{-1} = \cos(-\theta) + i\sin(-\theta) = \cos\theta - i\sin\theta$$

**Example:** Calculate $(1 + i)^{10}$.

**Solution:**

From polar form: $1 + i = \sqrt{2}(\cos\frac{\pi}{4} + i\sin\frac{\pi}{4})$

Therefore:
$$\begin{align}
(1 + i)^{10} &= (\sqrt{2})^{10}(\cos\frac{\pi}{4} + i\sin\frac{\pi}{4})^{10}\\
&= 2^5[\cos\frac{10\pi}{4} + i\sin\frac{10\pi}{4}]\\
&= 32[\cos\frac{5\pi}{2} + i\sin\frac{5\pi}{2}]\\
&= 32[0 + i \cdot 1] = 32i
\end{align}$$

**Example:** Use De Moivre's theorem to find a formula for $\cos(3\theta)$ in terms of $\cos\theta$.

**Solution:**

From De Moivre: $(\cos\theta + i\sin\theta)^3 = \cos(3\theta) + i\sin(3\theta)$

Expand the left side:
$$(\cos\theta + i\sin\theta)^3 = \cos^3\theta + 3i\cos^2\theta\sin\theta - 3\cos\theta\sin^2\theta - i\sin^3\theta$$

Equating real parts:
$$\cos(3\theta) = \cos^3\theta - 3\cos\theta\sin^2\theta = \cos^3\theta - 3\cos\theta(1-\cos^2\theta) = 4\cos^3\theta - 3\cos\theta$$



## 4. Inverse of Power: nth Roots

**Theorem:** The equation $z^n = w$ has exactly $n$ solutions in $\mathbb{C}$.

If $w = re^{i\theta}$, then the solutions are:
$$z_k = r^{1/n} e^{i(\theta + 2\pi k)/n}, \quad k = 0, 1, 2, \ldots, n-1$$

**Why $n$ roots?** Each time we add $2\pi$ to the angle of $w$, we get the same complex number. But when we take the $n$th root, these different representations give different values:
- $w = re^{i\theta} = re^{i(\theta + 2\pi)} = re^{i(\theta + 4\pi)} = \cdots$
- $w^{1/n}$ has angles: $\frac{\theta}{n}, \frac{\theta + 2\pi}{n}, \frac{\theta + 4\pi}{n}, \ldots$

These repeat after $n$ terms because $\frac{\theta + 2\pi n}{n} = \frac{\theta}{n} + 2\pi$.

**Geometric interpretation:** The $n$th roots of $w$ are evenly spaced around a circle of radius $r^{1/n}$, with angular spacing $\frac{2\pi}{n}$.

**Example:** Find all cube roots of $8i$.

**Solution:**

First, express in polar form: $8i = 8e^{i\pi/2}$

The cube roots are:
$$z_k = 8^{1/3} e^{i(\pi/2 + 2\pi k)/3} = 2e^{i\pi(1 + 4k)/6}, \quad k = 0, 1, 2$$

Computing each:
- $k = 0$: $z_0 = 2e^{i\pi/6} = 2(\cos\frac{\pi}{6} + i\sin\frac{\pi}{6}) = 2(\frac{\sqrt{3}}{2} + \frac{i}{2}) = \sqrt{3} + i$

- $k = 1$: $z_1 = 2e^{i5\pi/6} = 2(\cos\frac{5\pi}{6} + i\sin\frac{5\pi}{6}) = 2(-\frac{\sqrt{3}}{2} + \frac{i}{2}) = -\sqrt{3} + i$

- $k = 2$: $z_2 = 2e^{i3\pi/2} = 2(\cos\frac{3\pi}{2} + i\sin\frac{3\pi}{2}) = 2(0 - i) = -2i$

**Verification:** We can check $(−2i)^3 = −8i^3 = −8(−i) = 8i$ ✓

---



## Part II: The Complex Exponential Function

## 5. The Exponential Function

Recall from calculus that for real numbers $x$:
$$e^x = \sum_{n=0}^{\infty} \frac{x^n}{n!} = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \frac{x^4}{4!} + \cdots$$

This **Taylor series** converges for all real $x$ and has the fundamental property:
$$e^{x_1 + x_2} = e^{x_1} \cdot e^{x_2}$$

Extending to Complex Numbers, for any complex number $z = x + iy$, we define:
$$e^z = \sum_{n=0}^{\infty} \frac{z^n}{n!}$$

Does this definition make sense? We need to verify:
1. Does the series converge? Yes, by ratio test (omitted for the moment)
2. Does it preserve the fundamental property $e^{z_1 + z_2} = e^{z_1} e^{z_2}$?

$$\begin{align}
e^{z_1} \cdot e^{z_2} &= \left(\sum_{m=0}^{\infty}\frac{z_1^m}{m!}\right)\left(\sum_{n=0}^{\infty}\frac{z_2^n}{n!}\right)\\
&= \sum_{k=0}^{\infty}\left(\sum_{m=0}^{k}\frac{z_1^m}{m!}\frac{z_2^{k-m}}{(k-m)!}\right)
\end{align}$$

Factor out $\frac{1}{k!}$:
$$= \sum_{k=0}^{\infty}\frac{1}{k!}\left(\sum_{m=0}^{k}\frac{k!}{m!(k-m)!}z_1^m z_2^{k-m}\right)$$

Recognize the binomial coefficient $\binom{k}{m} = \frac{k!}{m!(k-m)!}$:
$$= \sum_{k=0}^{\infty}\frac{1}{k!}\left(\sum_{m=0}^{k}\binom{k}{m}z_1^m z_2^{k-m}\right)$$

By the binomial theorem:
$$= \sum_{k=0}^{\infty}\frac{(z_1 + z_2)^k}{k!} = e^{z_1 + z_2}$$

This proves the addition property! ✓

If you aren’t comfortable with the summation notations, here’s an alternative version:

Write out the products explicitly: $$e^{z_1} \cdot e^{z_2} = \left(1 + z_1 + \frac{z_1^2}{2!} + \frac{z_1^3}{3!} + \cdots\right)\left(1 + z_2 + \frac{z_2^2}{2!} + \frac{z_2^3}{3!} + \cdots\right)$$

Now group by total degree (powers that add to the same value):

**Degree 0:** $1$

**Degree 1:** $z_1 + z_2$

**Degree 2:** $\frac{z_1^2}{2!} + z_1 z_2 + \frac{z_2^2}{2!} = \frac{1}{2!}(z_1^2 + 2z_1z_2 + z_2^2) = \frac{(z_1+z_2)^2}{2!}$

**Degree 3:** $\frac{z_1^3}{3!} + \frac{z_1^2 z_2}{2!} + \frac{z_1 z_2^2}{2!} + \frac{z_2^3}{3!}$

Factor out $\frac{1}{3!}$: $$= \frac{1}{3!}\left(z_1^3 + 3z_1^2z_2 + 3z_1z_2^2 + z_2^3\right) = \frac{(z_1+z_2)^3}{3!}$$

**General degree k:** Collect all terms where the powers add to $k$: $$\frac{z_1^k}{k!} + \frac{z_1^{k-1}z_2}{(k-1)!} + \frac{z_1^{k-2}z_2^2}{(k-2)!2!} + \cdots + \frac{z_2^k}{k!}$$

Factor out $\frac{1}{k!}$: $$= \frac{1}{k!}\left(z_1^k + \frac{k!}{(k-1)!1!}z_1^{k-1}z_2 + \frac{k!}{(k-2)!2!}z_1^{k-2}z_2^2 + \cdots + z_2^k\right)$$

$$= \frac{1}{k!}\left(\binom{k}{0}z_1^k + \binom{k}{1}z_1^{k-1}z_2 + \binom{k}{2}z_1^{k-2}z_2^2 + \cdots + \binom{k}{k}z_2^k\right)$$

By the binomial theorem, this equals: $$= \frac{(z_1 + z_2)^k}{k!}$$

Therefore: $$e^{z_1} \cdot e^{z_2} = 1 + (z_1+z_2) + \frac{(z_1+z_2)^2}{2!} + \frac{(z_1+z_2)^3}{3!} + \cdots = e^{z_1 + z_2}$$

This proves the addition property! ✓

**Corollary:** For $z = x + iy$ where $x, y \in \mathbb{R}$: $$e^{x+iy} = e^x \cdot e^{iy}$$

This separates the real and imaginary contributions!



## 6. Euler's Formula

**Definition** of complex exponentials:

Let's understand the definition by substituting $z = i\theta$ (where $\theta$ is real) into the exponential series.

$$e^{i\theta} = \sum_{n=0}^{\infty}\frac{(i\theta)^n}{n!} = 1 + i\theta + \frac{(i\theta)^2}{2!} + \frac{(i\theta)^3}{3!} + \frac{(i\theta)^4}{4!} + \frac{(i\theta)^5}{5!} + \cdots$$

Now use the powers of $i$:

$$e^{i\theta} = 1 + i\theta - \frac{\theta^2}{2!} - i\frac{\theta^3}{3!} + \frac{\theta^4}{4!} + i\frac{\theta^5}{5!} - \frac{\theta^6}{6!} - i\frac{\theta^7}{7!} + \cdots$$

Separate real and imaginary parts, recall:

$$\cos\theta = \sum_{n=0}^{\infty}\frac{(-1)^n\theta^{2n}}{(2n)!} = 1 - \frac{\theta^2}{2!} + \frac{\theta^4}{4!} - \cdots$$

$$\sin\theta = \sum_{n=0}^{\infty}\frac{(-1)^n\theta^{2n+1}}{(2n+1)!} = \theta - \frac{\theta^3}{3!} + \frac{\theta^5}{5!} - \cdots$$

**Theorem (Euler's Formula):** $$\boxed{e^{i\theta} = \cos\theta + i\sin\theta}$$

This is one of the most beautiful formulas in all of mathematics!

**Special cases:**

- $e^{i\pi} = \cos\pi + i\sin\pi = -1 + 0i = -1$

  Therefore: $e^{i\pi} + 1 = 0$ (relating five fundamental constants!)

- $e^{i\pi/2} = \cos\frac{\pi}{2} + i\sin\frac{\pi}{2} = 0 + i = i$

- $e^{2\pi i} = \cos(2\pi) + i\sin(2\pi) = 1 + 0i = 1$



## Part III: Trigonometric Functions

## 7. Definition

From Euler's formula:
$$e^{iz} = \cos z + i\sin z$$
$$e^{-iz} = \cos(-z) + i\sin(-z) = \cos z - i\sin z$$

(using the fact that cosine is even and sine is odd)

Add these equations:
$$e^{iz} + e^{-iz} = 2\cos z$$

Subtract them:
$$e^{iz} - e^{-iz} = 2i\sin z$$

**Definition:** For any complex number $z$:
$$\cos z = \frac{e^{iz} + e^{-iz}}{2}$$
$$\sin z = \frac{e^{iz} - e^{-iz}}{2i}$$

These formulas extend sine and cosine to the entire complex plane.

**Property 1: Periodicity**

$$\cos(z + 2\pi) = \frac{e^{i(z+2\pi)} + e^{-i(z+2\pi)}}{2} = \frac{e^{iz}e^{2\pi i} + e^{-iz}e^{-2\pi i}}{2}$$

Since $e^{2\pi i} = \cos(2\pi) + i\sin(2\pi) = 1$:
$$= \frac{e^{iz} + e^{-iz}}{2} = \cos z$$

Similarly, $\sin(z + 2\pi) = \sin z$.

**Property 2: Even/Odd**

$$\cos(-z) = \frac{e^{-iz} + e^{iz}}{2} = \cos z \quad \text{(even)}$$
$$\sin(-z) = \frac{e^{-iz} - e^{iz}}{2i} = -\frac{e^{iz} - e^{-iz}}{2i} = -\sin z \quad \text{(odd)}$$

**Property 3: Values at Real Arguments**

When $z = x$ is real, the definitions reduce to the familiar real trigonometric functions.

$$\cos x = \frac{e^{ix} + e^{-ix}}{2} = \frac{(\cos x + i\sin x) + (\cos x - i\sin x)}{2} = \cos x$$ ✓

**Property 4: $\cos^2 z + \sin^2 z = 1$ for all complex $z$**

$$\begin{align}
\cos^2 z + \sin^2 z &= \left(\frac{e^{iz} + e^{-iz}}{2}\right)^2 + \left(\frac{e^{iz} - e^{-iz}}{2i}\right)^2\\
&= \frac{e^{2iz} + 2 + e^{-2iz}}{4} + \frac{e^{2iz} - 2 + e^{-2iz}}{-4} = 1
\end{align}$$



## 8. Trigonometric Identities

$$\sin(A + B) = \sin A \cos B + \cos A \sin B$$
$$\cos(A + B) = \cos A \cos B - \sin A \sin B$$

**Proof of cosine formula:** 

$$\begin{align}
\cos(A+B) &= \frac{e^{i(A+B)} + e^{-i(A+B)}}{2}\\
&= \frac{e^{iA}e^{iB} + e^{-iA}e^{-iB}}{2}\\
&= \frac{(\cos A + i\sin A)(\cos B + i\sin B) + (\cos A - i\sin A)(\cos B - i\sin B)}{2}\\
&= \cos A\cos B - \sin A\sin B
\end{align}$$

Setting $A = B = z$ in the addition formulas:

$$\sin(2z) = 2\sin z\cos z$$
$$\cos(2z) = \cos^2 z - \sin^2 z = 1 - 2\sin^2 z$$

$$\cos A \cos B = \frac{1}{2}[\cos(A+B) + \cos(A-B)]$$
$$\sin A \sin B = \frac{1}{2}[\cos(A-B) - \cos(A+B)]$$
$$\sin A \cos B = \frac{1}{2}[\sin(A+B) + \sin(A-B)]$$

**Proof of first formula:**

$$\begin{align}
\cos A\cos B &= \frac{1}{4}(e^{iA} + e^{-iA})(e^{iB} + e^{-iB})\\
&= \frac{1}{4}(e^{i(A+B)} + e^{i(A-B)} + e^{-i(A-B)} + e^{-i(A+B)})\\
&= \frac{1}{4}(e^{i(A+B)} + e^{-i(A+B)} + e^{i(A-B)} + e^{-i(A-B)})\\
&= \frac{1}{2}\left[\frac{e^{i(A+B)} + e^{-i(A+B)}}{2} + \frac{e^{i(A-B)} + e^{-i(A-B)}}{2}\right]\\
&= \frac{1}{2}[\cos(A+B) + \cos(A-B)]
\end{align}$$

Unlike real sine and cosine (which are bounded by 1), complex trigonometric functions can take arbitrarily large values.

$$\sin(iy) = \frac{e^{i(iy)} - e^{-i(iy)}}{2i} = \frac{e^{-y} - e^{y}}{2i} = \frac{-(e^{y} - e^{-y})}{2i} = i\frac{e^{y} - e^{-y}}{2} = i\sinh y$$

As $y \to \infty$, $\sinh y \to \infty$, so $|\sin(iy)| \to \infty$.

$$\sin(x+iy) = \sin x\cosh y + i\cos x\sinh y$$

$$|\sin(x+iy)|^2 = \sin^2 x\cosh^2 y + \cos^2 x\sinh^2 y$$

Using $\cosh^2 y - \sinh^2 y = 1$:
$$= \sin^2 x(1 + \sinh^2 y) + \cos^2 x\sinh^2 y = \sin^2 x + \sinh^2 y$$

So: $|\sin(x+iy)|^2 = \sin^2 x + \sinh^2 y$

**Zeros:**
$\sin z = 0$ if and only if $z = n\pi$ for some integer $n$.
$\cos z = 0$ if and only if $z = \frac{(2n+1)\pi}{2}$ for some integer $n$.

$$\sin z = 0 \Leftrightarrow \frac{e^{iz} - e^{-iz}}{2i} = 0 \Leftrightarrow e^{iz} = e^{-iz}$$
$\Leftrightarrow e^{2iz} = 1 = e^{2\pi i n}$
$\Leftrightarrow 2iz = 2\pi i n \Leftrightarrow z = n\pi$

$\cos z = 0 \Leftrightarrow \frac{e^{iz} + e^{-iz}}{2} = 0 \Leftrightarrow e^{iz} = -e^{-iz}$
$\Leftrightarrow e^{2iz} = -1 = e^{i\pi + 2\pi i n} = e^{i(2n+1)\pi}$
$\Leftrightarrow 2iz = i(2n+1)\pi \Leftrightarrow z = \frac{(2n+1)\pi}{2}$

The zeros of complex sine and cosine are exactly the same as for real sine and cosine
—they're all on the real axis!



##  9. Hyperbolic Functions

**Definition:**
$\cosh z = \frac{e^z + e^{-z}}{2}$
$\sinh z = \frac{e^z - e^{-z}}{2}$

**Why "hyperbolic"?** Just as $(\cos t, \sin t)$ parameterizes the unit circle $x^2 + y^2 = 1$, the pair $(\cosh t, \sinh t)$ parameterizes the unit hyperbola $x^2 - y^2 = 1$.

Compare the definitions:

**Trigonometric:**
$\cos z = \frac{e^{iz} + e^{-iz}}{2}, \quad \sin z = \frac{e^{iz} - e^{-iz}}{2i}$

**Hyperbolic:**
$\cosh z = \frac{e^z + e^{-z}}{2}, \quad \sinh z = \frac{e^z - e^{-z}}{2}$

**Key observation:** If we replace $z$ with $iz$ in the trigonometric functions:

$\cos(iz) = \frac{e^{i(iz)} + e^{-i(iz)}}{2} = \frac{e^{-z} + e^{z}}{2} = \cosh z$

$\sin(iz) = \frac{e^{i(iz)} - e^{-i(iz)}}{2i} = \frac{e^{-z} - e^{z}}{2i} = \frac{-(e^{z} - e^{-z})}{2i} = i\frac{e^{z} - e^{-z}}{2} = i\sinh z$

**Property 1: Even/Odd**

$\cosh(-z) = \frac{e^{-z} + e^{z}}{2} = \cosh z \quad \text{(even)}$

$\sinh(-z) = \frac{e^{-z} - e^{z}}{2} = -\sinh z \quad \text{(odd)}$

**Property 2: Hyperbolic Pythagorean Identity**

$\cosh^2 z - \sinh^2 z = 1$
$\begin{align}
\cosh^2 z - \sinh^2 z &= \left(\frac{e^z + e^{-z}}{2}\right)^2 - \left(\frac{e^z - e^{-z}}{2}\right)^2\\
&= \frac{(e^z + e^{-z})^2 - (e^z - e^{-z})^2}{4}\\
&= \frac{e^{2z} + 2 + e^{-2z} - e^{2z} + 2 - e^{-2z}}{4} = 1
\end{align}$

**Property 3: Addition Formulas**

$\sinh(A+B) = \sinh A\cosh B + \cosh A\sinh B$
$\cosh(A+B) = \cosh A\cosh B + \sinh A\sinh B$

**Note:** The sign in the cosine formula is **plus**, not minus!
$\begin{align}
\sinh(A+B) &= \frac{e^{A+B} - e^{-(A+B)}}{2}\\
&= \frac{e^A e^B - e^{-A}e^{-B}}{2}\\
&= \frac{1}{4}[(e^A + e^{-A})(e^B - e^{-B}) + (e^A - e^{-A})(e^B + e^{-B})]\\
&= \sinh A\cosh B + \cosh A\sinh B
\end{align}$

**Zeros: **
$\sinh z = 0$ if and only if $z = n\pi i$ for some integer $n$.
$\cosh z = 0$ if and only if $z = \frac{(2n+1)\pi i}{2}$ for some integer $n$.

Since $\sin(iz) = i\sinh z$:
$\sinh z = 0 \Leftrightarrow \sin(iz) = 0 \Leftrightarrow iz = n\pi \Leftrightarrow z = n\pi i$

Since $\cos(iz) = \cosh z$:
$\cosh z = 0 \Leftrightarrow \cos(iz) = 0 \Leftrightarrow iz = \frac{(2n+1)\pi}{2} \Leftrightarrow z = \frac{(2n+1)\pi i}{2}$

**Summary Table:**

| Function | Real Zeros | Complex Zeros |
|----------|-----------|---------------|
| $\sin z$ | $z = n\pi$ | Same (all real) |
| $\cos z$ | $z = \frac{(2n+1)\pi}{2}$ | Same (all real) |
| $\sinh z$ | $z = 0$ only | $z = n\pi i$ (purely imaginary) |
| $\cosh z$ | None | $z = \frac{(2n+1)\pi i}{2}$ (purely imaginary) |

**Geometric insight:** The transformation $z \mapsto iz$ is a 90° rotation in the complex plane. This rotation transforms:
- Real zeros → Imaginary zeros
- Oscillatory behavior → Exponential behavior
- Bounded functions → Unbounded functions

---



## Part IV: Complex Methods

## 10. The Complexification Technique

When faced with sums or products involving $\cos(f(x))$ or $\sin(f(x))$:

**Step 1: Complexify**

- Replace $\cos(f(x))$ with $\text{Re}(e^{if(x)})$
- Replace $\sin(f(x))$ with $\text{Im}(e^{if(x)})$

**Step 2: Compute with complex exponentials**

- Work with $e^{if(x)}$ using algebraic properties
- Exponentials multiply: $e^{if} \cdot e^{ig} = e^{i(f+g)}$
- Exponentials are easier to manipulate than trig functions

**Step 3: Extract the answer**

- Take the real part: $\text{Re}(e^{if(x)})$ returns to $\cos(f(x))$
- Take the imaginary part: $\text{Im}(e^{if(x)})$ returns to $\sin(f(x))$

**Key insight:** If $g(x)$ is real-valued, then: $$\cos(f(x)) \cdot g(x) = \text{Re}(e^{if(x)}) \cdot g(x) = \text{Re}(e^{if(x)} \cdot g(x))$$

This is because $g(x)$ is real, so multiplying by it doesn't affect which part is real or imaginary.

More generally, for real-valued functions $g(x)$ and $h(x)$: $$\cos(f(x)) \cdot g(x) + \sin(f(x)) \cdot h(x) = \text{Re}(e^{if(x)} \cdot g(x)) + \text{Im}(e^{if(x)} \cdot h(x))$$

**Bonus:** When computing complex expressions, you often get **both** sine and cosine results simultaneously: $$e^{i\theta} = \cos\theta + i\sin\theta$$



## 11.Trigonometric Summation

Problem: $S = \sum_{k=0}^{n} \cos(kx)$

Solution:

Use $\cos(kx) = \text{Re}(e^{ikx})$:
 $$S = \text{Re}\left(\sum_{k=0}^{n} e^{ikx}\right)$$

The sum is a geometric series with first term $1$ and common ratio $e^{ix}$:
 $$\sum_{k=0}^{n} e^{ikx} = \frac{1 - e^{i(n+1)x}}{1 - e^{ix}}$$

(provided $e^{ix} \neq 1$, i.e., $x \neq 2\pi m$)

To simplify, multiply numerator and denominator by $e^{-ix/2}$: $$= \frac{e^{-ix/2} - e^{i(n+1)x}e^{-ix/2}}{e^{-ix/2} - e^{ix/2}} = \frac{e^{-ix/2} - e^{inx+ix/2}}{-2i\sin(x/2)}$$

$$= \frac{e^{-ix/2} - e^{i(n+1/2)x}}{-2i\sin(x/2)}$$

Factor out $e^{inx/2}$ from the numerator: $$= \frac{e^{inx/2}(e^{-i(n+1)x/2} - e^{i(n+1)x/2})}{-2i\sin(x/2)} = \frac{e^{inx/2} \cdot (-2i\sin((n+1)x/2))}{-2i\sin(x/2)}$$

$$= e^{inx/2} \frac{\sin((n+1)x/2)}{\sin(x/2)}$$

Now $e^{inx/2} = \cos(nx/2) + i\sin(nx/2)$, so:

Taking the real part: $$\boxed{\sum_{k=0}^{n}\cos(kx) = \cos(nx/2)\frac{\sin((n+1)x/2)}{\sin(x/2)}}$$

Taking the imaginary part (bonus): $$\sum_{k=0}^{n}\sin(kx) = \sin(nx/2)\frac{\sin((n+1)x/2)}{\sin(x/2)}$$



## 12. Binomial-Trignometric Summation

Problem: $\sum_{k=0}^{n} \binom{n}{k}\cos(kx)$

**Solution:**

Using the complexification method: $$\sum_{k=0}^{n} \binom{n}{k}\cos(kx) = \text{Re}\left(\sum_{k=0}^{n} \binom{n}{k}e^{ikx}\right)$$

By the binomial theorem: $$\sum_{k=0}^{n} \binom{n}{k}e^{ikx} = (1 + e^{ix})^n$$

Now simplify $1 + e^{ix}$: $$1 + e^{ix} = 1 + \cos x + i\sin x$$

Using the half-angle approach: $$1 + e^{ix} = e^{ix/2}(e^{-ix/2} + e^{ix/2}) = e^{ix/2} \cdot 2\cos(x/2)$$

Therefore: $$(1 + e^{ix})^n = [2\cos(x/2)]^n \cdot e^{inx/2} = 2^n\cos^n(x/2)[\cos(nx/2) + i\sin(nx/2)]$$

Taking the real part: $$\boxed{\sum_{k=0}^{n} \binom{n}{k}\cos(kx) = 2^n\cos^n(x/2)\cos(nx/2)}$$

Taking the imaginary part(bonus): $$\sum_{k=0}^{n} \binom{n}{k}\sin(kx) = 2^n\cos^n(x/2)\sin(nx/2)$$



## 13.Trigonometric Integral

Problem: $I = \int_0^{\pi/2} \cos^6 x dx$.

**Traditional approach:** Use reduction formulas, which are messy and time-consuming.

**Complex solution:**

Use the identity $\cos x = \frac{e^{ix} + e^{-ix}}{2}$:
$\cos^6 x = \left(\frac{e^{ix} + e^{-ix}}{2}\right)^6 = \frac{1}{64}(e^{6ix} + 6e^{4ix} + 15e^{2ix} + 20 + 15e^{-2ix} + 6e^{-4ix} + e^{-6ix})$

Now integrate term by term from $0$ to $\pi/2$:

**For the constant term:** $\int_0^{\pi/2} 20 \, dx = 20 \cdot \frac{\pi}{2} = 10\pi$

**For exponential terms:** $\int_0^{\pi/2} e^{inx} \, dx = \left[\frac{e^{inx}}{in}\right]_0^{\pi/2} = \frac{e^{in\pi/2} - 1}{in}$

Let's check what happens:

- $\int_0^{\pi/2} e^{2ix} \, dx = \frac{e^{i\pi} - 1}{2i} = \frac{-1-1}{2i} = \frac{-2}{2i} = \frac{i}{1} = i$
- $\int_0^{\pi/2} e^{-2ix} \, dx = \frac{e^{-i\pi} - 1}{-2i} = \frac{-1-1}{-2i} = -i$

Similarly, other terms also cancel.

Therefore: $$I = \frac{1}{64}(10\pi + 0 + 0 + 0) = \frac{10\pi}{64} = \frac{5\pi}{32}$$

**Why the cancellation?** The function $\cos^6 x$ is real-valued, so when we expand it in terms of complex exponentials, the imaginary parts must cancel. Conjugate pairs $e^{inx}$ and $e^{-inx}$ always contribute equal and opposite imaginary parts to the integral.

This method works for any polynomial in $\sin x$ and $\cos x$ integrated over intervals of length that are multiples of $\pi$, or symmetric intervals around $0$.

**Key observations:**

- If $b - a = k\pi$ for integer $k$, then $\int_a^b e^{inx} \, dx = 0$ for all nonzero integers $n$
- Only the constant term contributes!
- For $\int_0^{\pi/2}$: Most terms vanish or cancel, but not all exponentials integrate to zero

**Limitations:**

- For non-polynomial functions (e.g., $\int \frac{dx}{2+\cos x}$), residue theory is needed
- For non-symmetric intervals, cancellation may not occur completely



## 14. Unity Roots

Problem: Prove that $\cos\frac{\pi}{7}\cos\frac{2\pi}{7}\cos\frac{3\pi}{7} = \frac{1}{8}$

**Complex solution:**

Let $\omega = e^{i\pi/7}$, so $\omega^7 = e^{i\pi} = -1$.

Using $\cos\theta = \frac{e^{i\theta} + e^{-i\theta}}{2}$:  $$\cos\frac{k\pi}{7} = \frac{\omega^k + \omega^{-k}}{2}$$

The product becomes: $$P = \cos\frac{\pi}{7}\cos\frac{2\pi}{7}\cos\frac{3\pi}{7} = \frac{(\omega+\omega^{-1})(\omega^2+\omega^{-2})(\omega^3+\omega^{-3})}{8}$$

Multiply out the numerator:

$$= \omega^6 + \omega^4 + \omega^2 + 1 + 1 + \omega^{-2} + \omega^{-4} + \omega^{-6}$$

Since $\omega^7 = -1$, we have $\omega^{-k} = \frac{1}{\omega^k} = \frac{\omega^7}{\omega^k} = -\omega^{7-k}$:

Substituting: $$= \omega^6 + \omega^4 + \omega^2 + 2 - \omega^5 - \omega^3 - \omega$$

Rearrange: $= \omega^6 - \omega^5 + \omega^4 - \omega^3 + \omega^2 - \omega + 2$

Now use the fact that $\omega^7 = -1$, which means $\omega^7 + 1 = 0$. 

Factoring: $\omega^7 + 1 = (\omega + 1)(\omega^6 - \omega^5 + \omega^4 - \omega^3 + \omega^2 - \omega + 1) = 0$

Since $\omega = e^{i\pi/7} \neq -1$, we must have: $\omega^6 - \omega^5 + \omega^4 - \omega^3 + \omega^2 - \omega + 1 = 0$

Therefore: $\omega^6 - \omega^5 + \omega^4 - \omega^3 + \omega^2 - \omega + 2 = 1$.  $$P = \frac{1}{8}$$.



## 15. Factorization

Problem: Factor $x^8 + x^4 + 1$ over the reals

**Complex Solution:**

Thinking of $w$ in the form $w^2+w+1$, we write $$x^{12} - 1 = (x^4)^3 - 1 = (x^4 - 1)((x^4)^2 + x^4 + 1) = (x^4 - 1)(x^8 + x^4 + 1)$$

$$x^8 + x^4 + 1 = \frac{x^{12} - 1}{x^4 - 1}$$

The roots of $x^{12} - 1 = 0$ are the 12th roots of unity: $e^{2\pi ik/12}$ for $k = 0, 1, \ldots, 11$.
The roots of $x^4 - 1 = 0$ are the 4th roots of unity: $e^{2\pi ik/4}$ for $k = 0, 1, 2, 3$.
Therefore, the roots of $x^8 + x^4 + 1$ are the 12th roots of unity that are NOT 4th roots of unity.
These are: $e^{2\pi ik/12}$ for $k = 1, 2, 4, 5, 7, 8, 10, 11$

Simplifying: $e^{i\pi/6}, e^{i\pi/3}, e^{i2\pi/3}, e^{i5\pi/6}, e^{i7\pi/6}, e^{i4\pi/3}, e^{i5\pi/3}, e^{i11\pi/6}$
Or: $e^{\pm i\pi/6}, e^{\pm i\pi/3}, e^{\pm i2\pi/3}, e^{\pm i5\pi/6}$

To factor over the reals, pair complex conjugate roots: $$(x - e^{i\theta})(x - e^{-i\theta}) = x^2 - (e^{i\theta} + e^{-i\theta})x + e^{i\theta}e^{-i\theta} = x^2 - 2\cos\theta \cdot x + 1$$

**Pair 1:** $\theta = \pi/6$ $$(x - e^{i\pi/6})(x - e^{-i\pi/6}) = x^2 - 2\cos(\pi/6)x + 1 = x^2 - \sqrt{3}x + 1$$
**Pair 2:** $\theta = \pi/3$ $$(x - e^{i\pi/3})(x - e^{-i\pi/3}) = x^2 - 2\cos(\pi/3)x + 1 = x^2 - x + 1$$
**Pair 3:** $\theta = 2\pi/3$ $$(x - e^{i2\pi/3})(x - e^{-i2\pi/3}) = x^2 - 2\cos(2\pi/3)x + 1 = x^2 + x + 1$$
**Pair 4:** $\theta = 5\pi/6$ $$(x - e^{i5\pi/6})(x - e^{-i5\pi/6}) = x^2 - 2\cos(5\pi/6)x + 1 = x^2 + \sqrt{3}x + 1$$

Therefore: $$\boxed{x^8 + x^4 + 1 = (x^2 - \sqrt{3}x + 1)(x^2 - x + 1)(x^2 + x + 1)(x^2 + \sqrt{3}x + 1)}$$

---



## Part V: Exercises

### Problem Set A: Polar Form and De Moivre

**A1.** Convert to polar form:
(a) $3 + 3i$
(b) $-1 + \sqrt{3}i$
(c) $-4i$
(d) $-2 - 2i$

**A2.** Convert to rectangular form:
(a) $2e^{i\pi/6}$
(b) $5e^{3i\pi/4}$
(c) $e^{-i\pi/3}$

**A3.** Compute using De Moivre's theorem:
(a) $(1 + i\sqrt{3})^6$
(b) $(\frac{1}{2} + \frac{\sqrt{3}}{2}i)^{12}$
(c) $(\cos\frac{\pi}{8} + i\sin\frac{\pi}{8})^{16}$

**A4.** Find all solutions:
(a) $z^4 = 16$
(b) $z^3 = -8$
(c) $z^6 = -1$

**A5.** Use De Moivre to prove:
(a) $\cos(4\theta) = 8\cos^4\theta - 8\cos^2\theta + 1$
(b) $\sin(5\theta)$ in terms of $\sin\theta$

### Problem Set B: Complex Exponentials

**B1.** Compute exactly:
(a) $|e^{2+3i}|$
(b) $e^{i\pi/3} \cdot e^{i\pi/6}$
(c) $(e^{i\pi/4})^{8}$

**B2.** Solve for all complex $z$:
(a) $e^z = 1$
(b) $e^z = -1$
(c) $e^z = i$
(d) $e^z = 2i$

**B3.** Prove that $|e^{iz}| = e^{-\text{Im}(z)}$ for all complex $z$.

**B4.** Show that $e^{z+2\pi i} = e^z$ for all $z$.

**B5.** Find all $z$ such that $e^z$ is:
(a) Real and positive
(b) Real and negative
(c) Purely imaginary

### Problem Set C: Trigonometric Functions

**C1.** Compute exactly (in $a + bi$ form):
(a) $\sin(i)$
(b) $\cos(i)$
(c) $\sin(1 + i)$
(d) $\cos(2i)$

**C2.** Solve for all complex $z$:
(a) $\sin z = 0$
(b) $\cos z = 0$
(c) $\sin z = 2$
(d) $\cos z = i$

**C3.** Prove the identities:
(a) $\sin(z + \pi) = -\sin z$
(b) $\cos(z + \pi) = -\cos z$
(c) $\sin(\pi/2 - z) = \cos z$
(d) $|\sin z|^2 + |\cos z|^2 = ?$ (Is it always 1?)

**C4.** Find all $z$ such that $\sin z = \cos z$.

### Problem Set D: Hyperbolic Functions

**D1.** Compute:
(a) $\sinh(i\pi/2)$
(b) $\cosh(i\pi)$
(c) $\sinh(\ln 2)$
(d) $\cosh(\ln 3)$

**D2.** Prove:
(a) $\sinh(2z) = 2\sinh z\cosh z$
(b) $\cosh(2z) = \cosh^2 z + \sinh^2 z$
(c) $\cosh z + \sinh z = e^z$
(d) $\cosh z - \sinh z = e^{-z}$

**D3.** Solve for all complex $z$:
(a) $\sinh z = 0$
(b) $\cosh z = 2$
(c) $\sinh z = i$

**D4.** Express in terms of trig functions:
(a) $\sinh(ix)$ where $x$ is real
(b) $\cosh(ix)$ where $x$ is real

### Problem Set E: Applications and Synthesis

**E1.** **Chebyshev Polynomials**: Define $T_n(\cos\theta) = \cos(n\theta)$.
(a) Show that $T_n(x)$ is indeed a polynomial in $x$.
(b) Find explicit formulas for $T_2(x), T_3(x), T_4(x)$.
(c) Prove that $T_n(x)$ satisfies: $T_{n+1}(x) = 2xT_n(x) - T_{n-1}(x)$.

**E2.** **Lagrange's trigonometric identities**:
Prove: $\sum_{k=0}^{n}\cos(kx) = \frac{\sin((n+1)x/2)\cos(nx/2)}{\sin(x/2)}$

**E3.** Evaluate:
(a) $\int_0^{2\pi} e^{\cos\theta} \cos(\sin\theta) d\theta$
(b) $\sum_{n=0}^{\infty} \frac{\cos(n\theta)}{2^n}$
(c) $\sum_{n=1}^{\infty} \frac{\sin(nx)}{n}$ for $0 < x < 2\pi$

**E4.** **Lucas's theorem on cube roots**:
Let $\omega = e^{2\pi i/3}$. Show that for any integers $a, b, c$:
$(a + b\omega + c\omega^2)(a + b\omega^2 + c\omega) = a^2 + b^2 + c^2 - ab - bc - ca$

**E5.** Prove that $\prod_{k=1}^{n-1}\sin\frac{k\pi}{n} = \frac{n}{2^{n-1}}$.

**E6.** **Partial fractions in the complex domain**:
Show that $\frac{1}{1-z^n} = \frac{1}{n}\sum_{k=0}^{n-1}\frac{1}{1-\omega^k z}$ where $\omega = e^{2\pi i/n}$.