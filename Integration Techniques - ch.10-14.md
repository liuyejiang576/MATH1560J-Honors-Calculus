## 10. Comprehensive Definite Integrals

### 10.1 Logarithmic-Trigonometric

**Example 10.1.1:** Evaluate $\int_0^1 \frac{\ln(1+x)}{1+x^2}dx$

**Solution: (King property after substitution):**

Let $x = \tan\theta$, so $dx = \sec^2\theta\,d\theta$, $1+x^2 = \sec^2\theta$

When $x=0$, $\theta=0$; when $x=1$, $\theta=\pi/4$:

$I = \int_0^{\pi/4} \frac{\ln(1+\tan\theta)}{\sec^2\theta} \sec^2\theta\,d\theta = \int_0^{\pi/4} \ln(1+\tan\theta)d\theta$

Now apply King property with $\pi/4 - \theta$: $I = \int_0^{\pi/4} \ln(1+\tan(\pi/4-\theta))d\theta$

Using $\tan(\pi/4-\theta) = \frac{1-\tan\theta}{1+\tan\theta}$:

$I = \int_0^{\pi/4} \ln\left(1 + \frac{1-\tan\theta}{1+\tan\theta}\right)d\theta = \int_0^{\pi/4} \ln\left(\frac{2}{1+\tan\theta}\right)d\theta$

$= \int_0^{\pi/4} [\ln 2 - \ln(1+\tan\theta)]d\theta = \frac{\pi}{4}\ln 2 - I$

Therefore: $2I = \frac{\pi}{4}\ln 2$, so $I = \frac{\pi}{8}\ln 2$

**Answer:** $\boxed{\frac{\pi}{8}\ln 2}$

------

**Example 10.1.2:** Evaluate $\int_0^{\pi/2} \ln(\sin x)dx$

**Solution:**

Let $I = \int_0^{\pi/2} \ln(\sin x)dx$

**Step 1:** By symmetry (substitution $u = \pi/2 - x$): $I = \int_0^{\pi/2} \ln(\cos x)dx$

**Step 2:** Add both: $2I = \int_0^{\pi/2} [\ln(\sin x) + \ln(\cos x)]dx = \int_0^{\pi/2} \ln(\sin x \cos x)dx$

$= \int_0^{\pi/2} \ln\left(\frac{\sin 2x}{2}\right)dx = \int_0^{\pi/2} [\ln(\sin 2x) - \ln 2]dx$

$= \int_0^{\pi/2} \ln(\sin 2x)dx - \frac{\pi}{2}\ln 2$

**Step 3:** For $\int_0^{\pi/2} \ln(\sin 2x)dx$, let $u = 2x$, $du = 2dx$:

$\int_0^{\pi/2} \ln(\sin 2x)dx = \frac{1}{2}\int_0^\pi \ln(\sin u)du$

**Step 4:** By symmetry on $[0,\pi]$ (since $\sin(\pi-u) = \sin u$): $\int_0^\pi \ln(\sin u)du = 2\int_0^{\pi/2} \ln(\sin u)du = 2I$

**Step 5:** Substitute back: $2I = \frac{1}{2} \cdot 2I - \frac{\pi}{2}\ln 2 = I - \frac{\pi}{2}\ln 2$

Therefore: $I = -\frac{\pi}{2}\ln 2$

**Answer:** $\boxed{-\frac{\pi}{2}\ln 2}$

------

### 10.2 Products and Quotients with Symmetry

**Example 10.2.1:** Evaluate $\int_0^{\pi/2} \frac{\sin^3 x}{\sin x + \cos x}dx$

**Solution:**

Let $I = \int_0^{\pi/2} \frac{\sin^3 x}{\sin x + \cos x}dx$

By King property with $\pi/2 - x$: $I = \int_0^{\pi/2} \frac{\cos^3 x}{\cos x + \sin x}dx$

Add: $2I = \int_0^{\pi/2} \frac{\sin^3 x + \cos^3 x}{\sin x + \cos x}dx$

Use the factorization: $a^3 + b^3 = (a+b)(a^2-ab+b^2)$:

$\sin^3 x + \cos^3 x = (\sin x + \cos x)(\sin^2 x - \sin x\cos x + \cos^2 x)$ $= (\sin x + \cos x)(1 - \sin x\cos x)$

Therefore: $2I = \int_0^{\pi/2} (1 - \sin x\cos x)dx = \int_0^{\pi/2} \left(1 - \frac{\sin 2x}{2}\right)dx$

$= \left[x + \frac{\cos 2x}{4}\right]_0^{\pi/2} = \left[\frac{\pi}{2} + \frac{-1}{4}\right] - \left[0 + \frac{1}{4}\right]$

$= \frac{\pi}{2} - \frac{1}{2}$

Therefore: $I = \frac{\pi}{4} - \frac{1}{4}$

------

**Example 10.2.2:** Evaluate $\int_0^{2\pi} \frac{dx}{(2+\cos x)^2}$

**Solution:**

Use periodicity and split the integral: $\int_0^{2\pi} \frac{dx}{(2+\cos x)^2} = 2\int_0^\pi \frac{dx}{(2+\cos x)^2}$

Now apply Weierstrass on $[0,\pi]$: when $x=\pi$, $t \to \infty$:

$2\int_0^\pi \frac{dx}{(2+\cos x)^2} = 2\int_0^\infty \frac{1}{(2 + \frac{1-t^2}{1+t^2})^2} \cdot \frac{2dt}{1+t^2}$

$= 4\int_0^\infty \frac{1}{(\frac{2(1+t^2) + 1-t^2}{1+t^2})^2} \cdot \frac{dt}{1+t^2}$

$= 4\int_0^\infty \frac{(1+t^2)^2}{(3+t^2)^2} \cdot \frac{dt}{1+t^2} = 4\int_0^\infty \frac{1+t^2}{(3+t^2)^2}dt$

Write: $\frac{1+t^2}{(3+t^2)^2} = \frac{(3+t^2) - 2}{(3+t^2)^2} = \frac{1}{3+t^2} - \frac{2}{(3+t^2)^2}$

$= 4\left[\int_0^\infty \frac{dt}{3+t^2} - 2\int_0^\infty \frac{dt}{(3+t^2)^2}\right]$

For the first: $\int_0^\infty \frac{dt}{3+t^2} = \frac{1}{\sqrt{3}}\arctan(t/\sqrt{3})\big|_0^\infty = \frac{\pi}{2\sqrt{3}}$

For the second, use the reduction formula or integrate by parts: $\int_0^\infty \frac{dt}{(t^2+3)^2} = \frac{1}{2 \cdot 3}\left[\frac{t}{t^2+3} + \arctan(t/\sqrt{3})/\sqrt{3}\right]_0^\infty = \frac{\pi}{12\sqrt{3}}$

Therefore: $= 4\left[\frac{\pi}{2\sqrt{3}} - 2 \cdot \frac{\pi}{12\sqrt{3}}\right] = \frac{4\pi\sqrt{3}}{9}$

------

### 10.3 Exponential-Trigonometric

**Example 10.3.1:** Evaluate $\int_0^{2\pi} e^{\cos x}\cos(\sin x)dx$

**Solution:**

Use Euler's formula: $e^{e^{i\theta}} = e^{\cos\theta}[\cos(\sin\theta) + i\sin(\sin\theta)]$

Consider: $\int_0^{2\pi} e^{\cos x}(\cos(\sin x) + i\sin(\sin x))dx = \int_0^{2\pi} e^{\cos x} e^{i\sin x}dx$

$= \int_0^{2\pi} e^{\cos x + i\sin x}dx = \int_0^{2\pi} e^{e^{ix}}dx$

Expand: $e^{e^{ix}} = \sum_{n=0}^\infty \frac{e^{inx}}{n!}$

Integrate term by term: $\int_0^{2\pi} e^{e^{ix}}dx = \sum_{n=0}^\infty \frac{1}{n!}\int_0^{2\pi} e^{inx}dx$

For $n \neq 0$: $\int_0^{2\pi} e^{inx}dx = \frac{e^{inx}}{in}\big|_0^{2\pi} = \frac{e^{2\pi in} - 1}{in} = 0$

For $n=0$: $\int_0^{2\pi} 1 \, dx = 2\pi$

Therefore: $\int_0^{2\pi} e^{e^{ix}}dx = 2\pi$

Taking the real part:

**Answer:** $\boxed{2\pi}$

------

## 11: Special Functions and Their Integrals

The functions in this chapter are often introduced as “given conclusions” in exercises, so you needn’t master their theories or derivations. Algebric manipulation is all your focus, which will be intensively tested in the examinations.

### 11.1 Gaussian Integral

The Gaussian integral is one of the most important definite integrals in mathematics, with applications spanning probability theory, physics, and engineering:

$$\int_{-\infty}^{\infty} e^{-x^2} dx = \sqrt{\pi}$$

For the one-sided version:
$$\int_{0}^{\infty} e^{-x^2} dx = \frac{\sqrt{\pi}}{2}$$

**Proof:** Let $I = \int_{-\infty}^{\infty} e^{-x^2} dx$. Then:

$$I^2 = \left(\int_{-\infty}^{\infty} e^{-x^2} dx\right)\left(\int_{-\infty}^{\infty} e^{-y^2} dy\right) = \int_{-\infty}^{\infty}\int_{-\infty}^{\infty} e^{-(x^2+y^2)} dxdy$$

Switching to polar coordinates: $x = r\cos\theta$, $y = r\sin\theta$, $dxdy = rdrd\theta$

$$I^2 = \int_{0}^{2\pi}\int_{0}^{\infty} e^{-r^2} rdrd\theta = \int_{0}^{2\pi} d\theta \cdot \int_{0}^{\infty} re^{-r^2} dr$$

$$= 2\pi \cdot \left[-\frac{1}{2}e^{-r^2}\right]_{0}^{\infty} = 2\pi \cdot \frac{1}{2} = \pi$$

Therefore: $I = \sqrt{\pi}$

**Moments of Gaussian Distribution:**

For $n \geq 0$ and $a > 0$:
$$\int_{0}^{\infty} x^{2n} e^{-ax^2} dx = \frac{(2n-1)!!}{2^{n+1}a^n}\sqrt{\frac{\pi}{a}}$$
$$\int_{0}^{\infty} x^{2n+1} e^{-ax^2} dx = \frac{n!}{2a^{n+1}}$$

where $(2n-1)!! = 1\cdot 3\cdot 5\cdots(2n-1)$ is the double factorial.

**Derivation via Parameter Differentiation:**

Consider $I(a) = \int_{0}^{\infty} e^{-ax^2} dx = \frac{1}{2}\sqrt{\frac{\pi}{a}}$

Differentiating under the integral sign:
$$\frac{d^n}{da^n}I(a) = (-1)^n \int_{0}^{\infty} x^{2n} e^{-ax^2} dx = \frac{d^n}{da^n}\left(\frac{1}{2}\sqrt{\frac{\pi}{a}}\right)$$

---

**Example 11.1.1:** Evaluate $\int_{0}^{\infty} x^2 e^{-x^2} dx$

Consider the parameterized integral:
$$I(\alpha) = \int_0^\infty e^{-\alpha x^2} dx = \frac{1}{2}\sqrt{\frac{\pi}{\alpha}}$$

Differentiate with respect to $\alpha$:
$$I'(\alpha) = \frac{d}{d\alpha}\int_0^\infty e^{-\alpha x^2} dx = \int_0^\infty \frac{\partial}{\partial\alpha}e^{-\alpha x^2} dx = -\int_0^\infty x^2 e^{-\alpha x^2} dx$$

Also, from the closed form:
$$I'(\alpha) = -\frac{1}{4}\sqrt{\pi}\alpha^{-3/2}$$

Evaluate at $\alpha = 1$:
$$-\int_0^\infty x^2 e^{-x^2} dx = -\frac{1}{4}\sqrt{\pi}$$
$$\int_0^\infty x^2 e^{-x^2} dx = \frac{\sqrt{\pi}}{4}$$

**Connection to Error Function:**
The error function is defined as $\text{erf}(x) = \frac{2}{\sqrt{\pi}}\int_0^x e^{-t^2}dt$. Our integral represents a moment of the Gaussian distribution.

---

**Example 11.1.2:** Evaluate $\int_{0}^{\infty} \frac{1 - e^{-x^2}}{x^2} dx$

(MATH1560J 2021 Second Midterm Examination, Exercise 3)

**Solution 1: Integration by Parts**

Let $u = 1 - e^{-x^2}$, $dv = \frac{dx}{x^2}$, so $du = 2xe^{-x^2}dx$, $v = -\frac{1}{x}$:

$$\int \frac{1 - e^{-x^2}}{x^2} dx = -\frac{1}{x}(1 - e^{-x^2}) + \int \frac{1}{x} \cdot 2xe^{-x^2}dx$$
$$= -\frac{1}{x}(1 - e^{-x^2}) + 2\int e^{-x^2}dx$$

Therefore:
$$\int_0^\infty \frac{1 - e^{-x^2}}{x^2} dx = \left[-\frac{1}{x}(1 - e^{-x^2})\right]_0^\infty + 2\int_0^\infty e^{-x^2}dx$$

Evaluate the boundary terms:

- $\lim_{x \to \infty} \frac{1 - e^{-x^2}}{x} = 0$ 
- $\lim_{x \to 0} \frac{1 - e^{-x^2}}{x} = \lim_{x \to 0} \frac{2xe^{-x^2}}{1} = 0$ 

Using the known Gaussian integral $\int_{-\infty}^\infty e^{-x^2}dx = \sqrt{\pi}$:

$$\int_0^\infty \frac{1 - e^{-x^2}}{x^2} dx = 0 + \int_{-\infty}^\infty e^{-x^2}dx = \sqrt{\pi}$$

**Solution 2: Parameter Differentiation**

Let $I(\alpha) = \int_0^\infty \frac{1 - e^{-\alpha x^2}}{x^2} dx$

Differentiate with respect to $\alpha$:
$$I'(\alpha) = \int_0^\infty \frac{\partial}{\partial\alpha}\left(\frac{1 - e^{-\alpha x^2}}{x^2}\right) dx = \int_0^\infty e^{-\alpha x^2} dx = \frac{1}{2}\sqrt{\frac{\pi}{\alpha}}$$

Integrate back:
$$I(\alpha) = \int \frac{1}{2}\sqrt{\frac{\pi}{\alpha}} d\alpha = \sqrt{\pi\alpha} + C$$

Since $I(0) = 0$, we have $C = 0$, so $I(\alpha) = \sqrt{\pi\alpha}$

For $\alpha = 1$: $$\boxed{\sqrt{\pi}}$$

---

### 11.2 Error Function

The error function is a special function that arises naturally in probability, statistics, and the study of heat diffusion. It is defined as:

$$\text{erf}(x) = \frac{2}{\sqrt{\pi}}\int_0^x e^{-t^2}dt$$

The complementary error function is: $$\text{erfc}(x) = 1 - \text{erf}(x) = \frac{2}{\sqrt{\pi}}\int_x^\infty e^{-t^2}dt$$

**Key Properties:**

1. $\text{erf}(0) = 0$
2. $\text{erf}(\infty) = 1$
3. $\text{erf}(-x) = -\text{erf}(x)$ (odd function)
4. $\frac{d}{dx}\text{erf}(x) = \frac{2}{\sqrt{\pi}}e^{-x^2}$

**Connection to Gaussian Integral:**

From the Gaussian integral $\int_{-\infty}^{\infty} e^{-x^2} dx = \sqrt{\pi}$, we have: $$\int_0^\infty e^{-x^2} dx = \frac{\sqrt{\pi}}{2}$$

Therefore: $$\lim_{x \to \infty} \text{erf}(x) = \frac{2}{\sqrt{\pi}} \cdot \frac{\sqrt{\pi}}{2} = 1$$

------

**Example 11.2.1:** Show that $\int_{-\infty}^{\infty} e^{-(x-\mu)^2/(2\sigma^2)} dx = \sqrt{2\pi}\sigma$

**Solution:**

Let $u = \frac{x-\mu}{\sqrt{2}\sigma}$, then $du = \frac{dx}{\sqrt{2}\sigma}$, so $dx = \sqrt{2}\sigma \, du$:

$$\int_{-\infty}^{\infty} e^{-(x-\mu)^2/(2\sigma^2)} dx = \int_{-\infty}^{\infty} e^{-u^2} \cdot \sqrt{2}\sigma , du$$

$$= \sqrt{2}\sigma \int_{-\infty}^{\infty} e^{-u^2} du = \sqrt{2}\sigma \cdot \sqrt{\pi} = \sqrt{2\pi}\sigma$$

**Connection to Probability:** This integral shows that the Gaussian (normal) distribution with mean $\mu$ and standard deviation $\sigma$ is properly normalized.

------

**Connection to Normal Distribution:**

The probability density function of the standard normal distribution is: $$\phi(x) = \frac{1}{\sqrt{2\pi}}e^{-x^2/2}$$

The cumulative distribution function is: $$\Phi(x) = \int_{-\infty}^x \phi(t) dt = \frac{1}{2}\left[1 + \text{erf}\left(\frac{x}{\sqrt{2}}\right)\right]$$

This shows how the error function naturally appears in probability and statistics.


---

### 11.3 Gamma function $\int_0^\infty u^n e^{-u} du = n!$

**Example 11.3.1:** Show that: $$\int_0^1 x^x dx = \sum_{n=1}^{\infty} (-1)^{n+1} n^{-n}$$

(MATH1560J 2021 Final Examination, Exercise 6)

**Solution:**

Express $x^x$ using the exponential function:
$$x^x = e^{x\ln x} = \sum_{n=0}^{\infty} \frac{(x\ln x)^n}{n!}$$

Integrate term by term:
$$\int_0^1 x^x dx = \sum_{n=0}^{\infty} \frac{1}{n!} \int_0^1 x^n (\ln x)^n dx$$

For the integral $\int_0^1 x^n (\ln x)^n dx$, use the substitution $t = -\ln x$, so $x = e^{-t}$, $dx = -e^{-t} dt$. When $x=0$, $t \to \infty$; when $x=1$, $t=0$:

$$\int_0^1 x^n (\ln x)^n dx = \int_\infty^0 (e^{-t})^n (-t)^n (-e^{-t}) dt$$

$$= (-1)^{n+1} \int_\infty^0 t^n e^{-(n+1)t} dt$$

$$ = (-1)^n \int_0^\infty t^n e^{-(n+1)t} dt$$

Now substitute $u = (n+1)t$, $dt = \frac{du}{n+1}$:
$$ = (-1)^n \int_0^\infty \left(\frac{u}{n+1}\right)^n e^{-u} \frac{du}{n+1}$$
$$ = (-1)^n (n+1)^{-(n+1)} \int_0^\infty u^n e^{-u} du$$

Using the Gamma function identity $\int_0^\infty u^n e^{-u} du = n!$:

$$\int_0^1 x^n (\ln x)^n dx = (-1)^n (n+1)^{-(n+1)} n!$$

Substitute back:
$$\int_0^1 x^x dx = \sum_{n=0}^{\infty} \frac{1}{n!} \cdot (-1)^n (n+1)^{-(n+1)} n! = \sum_{n=0}^{\infty} (-1)^n (n+1)^{-(n+1)}$$

Reindex by letting $m = n+1$:
$$= \sum_{m=1}^{\infty} (-1)^{m-1} m^{-m} = \sum_{m=1}^{\infty} (-1)^{m+1} m^{-m}$$

**Final Answer:** $$\boxed{\sum_{n=1}^{\infty} (-1)^{n+1} n^{-n}}$$

---

### 11.4 Sine Integral $\int_0^\infty \frac{\sin(ax)}{x} dx = \frac{\pi}{2}$

This is a conclusion of Dirichlet integral, for $a>0$.

**Example 11.4.1:** Evaluate $\int_0^\infty \frac{1 - \cos(ax)}{x^2} dx$

**Solution:**
Let $F(a) = \int_0^\infty \frac{1 - \cos(ax)}{x^2} dx$
$$F'(a) = \frac{d}{da}\int_0^\infty \frac{1 - \cos(ax)}{x^2} dx = \int_0^\infty \frac{\partial}{\partial a}\left(\frac{1 - \cos(ax)}{x^2}\right) dx$$
$$= \int_0^\infty \frac{\sin(ax)}{x} dx = \frac{\pi}{2}$$

Integrate Back:
$$F(a) = \int \frac{\pi}{2} da = \frac{\pi}{2}a + C$$

Determine Constant
When $a = 0$: $F(0) = \int_0^\infty \frac{1 - 1}{x^2} dx = 0$, so $C = 0$

$$\boxed{\frac{\pi}{2}a}$$

**Connection to Sine Integral:**
The sine integral is defined as $\text{Si}(x) = \int_0^x \frac{\sin t}{t}dt$. Our result shows how integrals of this family can be evaluated without explicit reference to $\text{Si}(x)$.

---

**Example 11.4.2:** Evaluate $\int_0^\infty \frac{\sin^3 x}{x} dx$

**Solution:**

**Step 1: Trigonometric Identity**
Use the triple-angle identity: $\sin^3 x = \frac{3\sin x - \sin 3x}{4}$

**Step 2: Split the Integral**
$$\int_0^\infty \frac{\sin^3 x}{x} dx = \frac{1}{4}\int_0^\infty \frac{3\sin x - \sin 3x}{x} dx$$
$$= \frac{3}{4}\int_0^\infty \frac{\sin x}{x} dx - \frac{1}{4}\int_0^\infty \frac{\sin 3x}{x} dx$$

**Step 3: Known Dirichlet Integral**
We know: $\int_0^\infty \frac{\sin(kx)}{x} dx = \frac{\pi}{2}$ for $k > 0$

**Final Answer:**
$$\boxed{\frac{\pi}{4}}$$

**Connection to Sine Integral:**
This demonstrates how even when individual terms involve the sine integral $\text{Si}(x)$, certain combinations yield elementary results.

---

### 12. Equalities and Inequalities

We have focused primarily on computing antiderivatives and evaluating definite integrals. Moreover, the integral calculus provides a framework for establishing deep mathematical relationships and proving fundamental inequalities. The techniques developed here—symmetry exploitation, parameter differentiation, and strategic substitutions—synthesize many of the methods we have studied in previous chapters.

---

**Example 12.1.1:** (MATH1560J 2021 Second Midterm Examination, Exercise 7)

**(i)** Show that for any convergent function $f$:

$$\int_{-\infty}^{\infty} f\left(x - \frac{1}{x}\right) dx = \int_{-\infty}^{\infty} f(x) dx$$

**(ii)** Evaluate: $$\int_{-\infty}^{\infty} \exp\left(-x^2 - \frac{\alpha}{x^2}\right) dx$$ where $\alpha > 0$

**Solution:**

**(i)** Let $I = \int_{-\infty}^{\infty} f\left(x - \frac{1}{x}\right) dx$

Make substitution $y = -\frac{1}{x}$, then $dy = \frac{dx}{x^2}$, and:

$$I = \int_{-\infty}^{\infty} f\left(-\frac{1}{y} + y\right) \frac{dy}{y^2} = \int_{-\infty}^{\infty} f\left(y - \frac{1}{y}\right) \frac{dy}{y^2}$$

Add both expressions:

$$2I = \int_{-\infty}^{\infty} f\left(x - \frac{1}{x}\right) \left(1 + \frac{1}{x^2}\right) dx$$

Now substitute $u = x - \frac{1}{x}$, then $du = \left(1 + \frac{1}{x^2}\right) dx$

As $x$ goes from $-\infty$ to $0$ and from $0$ to $\infty$, $u$ goes from $-\infty$ to $\infty$ twice:

$$2I = 2\int_{-\infty}^{\infty} f(u) du$$

Therefore: $I = \int_{-\infty}^{\infty} f(u) du$

**(ii)** Complete the square:

$$-x^2 - \frac{\alpha}{x^2} = -\left(x - \frac{\sqrt{\alpha}}{x}\right)^2 - 2\sqrt{\alpha}$$

Therefore:

$$\int_{-\infty}^{\infty} \exp\left(-x^2 - \frac{\alpha}{x^2}\right) dx = e^{-2\sqrt{\alpha}} \int_{-\infty}^{\infty} \exp\left[-\left(x - \frac{\sqrt{\alpha}}{x}\right)^2\right] dx$$

By part (i) with $f(u) = e^{-u^2}$:

$$= e^{-2\sqrt{\alpha}} \int_{-\infty}^{\infty} e^{-u^2} du = e^{-2\sqrt{\alpha}} \sqrt{\pi}$$

**Final Answer:** $$\boxed{\sqrt{\pi}e^{-2\sqrt{\alpha}}}$$

---

**Example 12.1.2** Given $f\in C^{1}[0,1]$ and $f(0)=f(1)=-1/6$, prove:

$\int_{0}^{1}(f')^{2}\,dx\ge2\int_{0}^{1}f\,dx+\frac{1}{4}$.

Try $I = \int_{0}^{1}\bigl(f'(x)+x\bigr)^{2}\,dx\ge0$, then $\frac{1}{4}$ is missing. We need to minimize $\int_{0}^{1}(x-a)^{2}\,dx$, then we choose $a = \frac{1}{2}$.

We define $I = \int_{0}^{1}\bigl(f'(x)+x-\tfrac{1}{2}\bigr)^{2}\,dx\ge0$.

Expanding the binomial inside the integral:
$$\begin{aligned} I &= \int_{0}^{1}\left[(f'(x))^{2} + 2f'(x)(x-\tfrac{1}{2}) + (x-\tfrac{1}{2})^{2}\right]\,dx \\ &= \underbrace{\int_{0}^{1}(f'(x))^{2}\,dx}_{I_1} + \underbrace{2\int_{0}^{1}f'(x)(x-\tfrac{1}{2})\,dx}_{I_2} + \underbrace{\int_{0}^{1}(x-\tfrac{1}{2})^{2}\,dx}_{I_3}\end{aligned}$$

Evaluate $I_2$ using Integration by Parts (IBP)

Set $u=x-\frac{1}{2}$ and $dv=f'(x)\,dx$. Then $du=dx$ and $v=f(x)$.

$$I_{2} = 2\left(\left[f(x)(x-\tfrac{1}{2})\right]_{0}^{1} - \int_{0}^{1}f(x)\,dx\right)$$

$$\begin{aligned} \left[f(x)(x-\tfrac{1}{2})\right]_{0}^{1} &= f(1)(1-\tfrac{1}{2}) - f(0)(0-\tfrac{1}{2}) \\ &= (-\tfrac{1}{6})(\tfrac{1}{2}) - (-\tfrac{1}{6})(-\tfrac{1}{2}) = -\frac{1}{6}\end{aligned}$$

$$I_{2} = 2\left(-\frac{1}{6} - \int_{0}^{1}f(x)\,dx\right) = -\frac{1}{3} - 2\int_{0}^{1}f(x)\,dx$$

$$I_{3} = \int_{0}^{1}(x-\tfrac{1}{2})^{2}\,dx = \left[\frac{(x-1/2)^{3}}{3}\right]_{0}^{1}$$$$I_{3} = \frac{(1/2)^{3}}{3} - \frac{(-1/2)^{3}}{3} = \frac{1}{24} + \frac{1}{24} = \frac{2}{24} = \frac{1}{12}$$

Substitute $I_2$ and $I_3$ back into the inequality $I_1 + I_2 + I_3 \ge 0$:

$$\int_{0}^{1}(f'(x))^{2}\,dx + \left(-\frac{1}{3} - 2\int_{0}^{1}f(x)\,dx\right) + \frac{1}{12} \ge 0$$

$$\int_{0}^{1}(f'(x))^{2}\,dx \ge 2\int_{0}^{1}f(x)\,dx + \frac{1}{3} - \frac{1}{12}$$$$\int_{0}^{1}(f'(x))^{2}\,dx \ge 2\int_{0}^{1}f(x)\,dx + \frac{4-1}{12}$$

$$\int_{0}^{1}(f'(x))^{2}\,dx \ge 2\int_{0}^{1}f(x)\,dx + \frac{1}{4}$$

The proof is complete.

---

**Example 12.1.3:**
(i) Prove the Cauchy-Schwarz Inequality for Integrals:

 $$\int_0^1 f(x)g(x) dx \leq \sqrt{\int_0^1 f^2(x) dx} \cdot \sqrt{\int_0^1 g^2(x) dx}$$

(ii) Given $f \in C[0,1]$ with $f(x) \geq 0$ and $\int_0^1 f(x) dx = 1$. 

Prove: $$\int_0^1 xf(x) dx \cdot \int_0^1 \frac{f(x)}{x} dx \geq 1$$

**Solution:**

Consider the function $h(t) = \int_0^1 [f(x) + tg(x)]^2 dx \geq 0$ for all $t \in \mathbb{R}$.

Expanding: $$h(t) = \int_0^1 f^2(x) dx + 2t\int_0^1 f(x)g(x) dx + t^2\int_0^1 g^2(x) dx$$

Let:

- $A = \int_0^1 f^2(x) dx$
- $B = \int_0^1 f(x)g(x) dx$
- $C = \int_0^1 g^2(x) dx$

Then: $h(t) = A + 2Bt + Ct^2 \geq 0$ for all $t$

Since this quadratic is non-negative for all $t$, its discriminant must be non-positive: $$\Delta = (2B)^2 - 4AC \leq 0$$

$$\left|\int_0^1 f(x)g(x) dx\right| \leq \sqrt{\int_0^1 f^2(x) dx} \cdot \sqrt{\int_0^1 g^2(x) dx}$$

**Equality holds** when $f(x) = \lambda g(x)$ for some constant $\lambda$.



Apply Cauchy-Schwarz inequality with $g(x) = \sqrt{xf(x)}$ and $h(x) = \frac{\sqrt{f(x)}}{\sqrt{x}}$:

$$\left(\int_0^1 g(x)h(x) dx\right)^2 \leq \int_0^1 g^2(x) dx \cdot \int_0^1 h^2(x) dx$$

$$\left(\int_0^1 \sqrt{xf(x)} \cdot \frac{\sqrt{f(x)}}{\sqrt{x}} dx\right)^2 \leq \int_0^1 xf(x) dx \cdot \int_0^1 \frac{f(x)}{x} dx$$

$$\left(\int_0^1 f(x) dx\right)^2 \leq \int_0^1 xf(x) dx \cdot \int_0^1 \frac{f(x)}{x} dx$$

Since $\int_0^1 f(x) dx = 1$:

$$1 \leq \int_0^1 xf(x) dx \cdot \int_0^1 \frac{f(x)}{x} dx$$

------

**Example 12.1.4:** Show that:

(i) For $a, b > 0$: $$\int_0^{\infty} e^{-ax}\sin(bx) dx = \frac{b}{a^2+b^2}$$

(ii) $$\int_0^{\infty} \frac{e^{-ax} - e^{-bx}}{x}\sin x \, dx = \arctan b - \arctan a$$

**Solution:**

**Part 1:** Standard integral using integration by parts twice, or complex exponentials:

$$\int_0^{\infty} e^{-ax}\sin(bx) dx = \text{Im}\left(\int_0^{\infty} e^{(-a+ib)x} dx\right)$$

$$= \text{Im}\left(\frac{1}{-a+ib}\right) = \text{Im}\left(\frac{-a-ib}{a^2+b^2}\right) = \frac{b}{a^2+b^2}$$

**Part 2:** Let $I(a) = \int_0^{\infty} \frac{e^{-ax}\sin x}{x} dx$

Then: $$I'(a) = -\int_0^{\infty} e^{-ax}\sin x \, dx = -\frac{1}{a^2+1}$$

Integrate: $$I(a) = -\arctan a + C$$

As $a \to \infty$, $I(a) \to 0$, so $C = \frac{\pi}{2}$

Therefore: $I(a) = \frac{\pi}{2} - \arctan a$

Finally: $$\int_0^{\infty} \frac{e^{-ax} - e^{-bx}}{x}\sin x \, dx = I(a) - I(b) = \arctan b - \arctan a$$



------

## Part VII: Non-Elementary Integrals and Final Topics

轻舟已过万重山。

### 13. Recognition of Non-Elementary Forms

Some integrals cannot be expressed in terms of elementary functions (polynomials, exponentials, logarithms, trigonometric functions, and their inverses).

------

### 13.1 Elliptic Integrals

**Form 1:** $\int \frac{dx}{\sqrt{P(x)}}$ where $P(x)$ is a polynomial of degree 3 or 4

**Form 2:** $\int \sqrt{P(x)} \, dx$ where $P(x)$ is a polynomial of degree 3 or 4

**Example:** $\int \frac{dx}{\sqrt{x^3-1}}$ (elliptic integral of the first kind)

**Example:** $\int \sqrt{\sin x} \, dx$ cannot be expressed in elementary functions

------

### 13.2 Other Non-Elementary Forms

**Common non-elementary integrals:**

1. **Error function:** $\int e^{-x^2}dx = \frac{\sqrt{\pi}}{2}\text{erf}(x) + C$
2. **Sine integral:** $\int \frac{\sin x}{x}dx = \text{Si}(x) + C$
3. **Logarithmic integral:** $\int \frac{dx}{\ln x} = \text{Li}(x) + C$
4. **Fresnel integrals:** $\int \sin(x^2)dx$ and $\int \cos(x^2)dx$
5. **Exponential integral:** $\int \frac{e^x}{x}dx = \text{Ei}(x) + C$

------

### 13.3 When to Stop

**Decision criteria for recognizing non-elementary integrals:**

1. **Check standard forms:** Compare against known non-elementary patterns
2. **Risch algorithm:** Theoretical (but complex) algorithm determines if elementary antiderivative exists
3. **Computer algebra systems:** Programs like Mathematica can detect non-elementary integrals
4. **Liouville's theorem:** Provides theoretical framework for impossibility proofs

**What to do when integral is non-elementary:**

- Express as a special function (if standard)
- Use numerical methods (trapezoidal rule, Simpson's rule, Gaussian quadrature)
- Series expansion for approximation
- Asymptotic methods for large parameter limits

**Numerical methods overview:**

**Trapezoidal Rule:** $\int_a^b f(x)dx \approx \frac{b-a}{2n}\left[f(x_0) + 2\sum_{i=1}^{n-1}f(x_i) + f(x_n)\right]$

**Simpson's Rule:** $\int_a^b f(x)dx \approx \frac{b-a}{3n}\left[f(x_0) + 4\sum_{i=1,3,5,...}f(x_i) + 2\sum_{i=2,4,6,...}f(x_i) + f(x_n)\right]$

------

## 14. Summary

14.1 Method Decision Tree

```
START: ∫f(x)dx
│
├─ Is it a standard form?
│  ├─ YES → Apply direct formula
│  └─ NO → Continue
│
├─ Is f(x) rational (P(x)/Q(x))?
│  ├─ YES → 
│  │  ├─ deg(P) ≥ deg(Q)? → Long division first
│  │  └─ Partial fractions
│  └─ NO → Continue
│
├─ Does it contain radicals?
│  ├─ √(ax²+bx+c) → Complete square → Trig substitution
│  ├─ √(ax+b), √(cx+d) → Rationalize via LCM substitution
│  └─ √(P(x)), deg(P)≥3 → Check if elliptic (non-elementary)
│
├─ Does it contain products?
│  ├─ Polynomial × Exponential → IBP (tabular method)
│  ├─ Polynomial × Trig → IBP (reduction formulas)
│  ├─ Exponential × Trig → 
│  │  ├─ Double IBP (traditional)
│  │  └─ Complex exponentials (Euler)
│  ├─ Trig × Trig → Product-to-sum identities
│  └─ Mixed types → IBP or substitution
│
├─ Pure trigonometric powers?
│  ├─ sin^m(x)cos^n(x) →
│  │  ├─ One power odd? → Save factor, substitute
│  │  ├─ Both even? → Half-angle formulas or complex method
│  │  └─ High even powers? → Complex exponentials
│  ├─ tan^n(x), sec^n(x) → 
│  │  ├─ Use tan²+1=sec²
│  │  └─ Reduction formulas
│  └─ Hyperbolic → Similar strategies
│
├─ Contains inverse functions?
│  ├─ arcsin, arctan, ln, etc. → IBP with u=inverse function
│  └─ Powers of inverse functions → Reduction formulas
│
├─ Definite integral with symmetry?
│  ├─ Check King property: x → a+b-x
│  ├─ Check even/odd: f(-x) = ±f(x)
│  ├─ Check periodicity
│  └─ Feynman's trick (parameter differentiation)
│
└─ Still stuck?
   ├─ Try multiple substitutions
   ├─ Check if non-elementary
   └─ You made a mistake in previous calculations
```

------

### 14.2 Common Pitfalls

**1. Forgetting absolute value in logarithms**

❌ Wrong: $\int \frac{dx}{x} = \ln(x) + C$

✓ Correct: $\int \frac{dx}{x} = \ln|x| + C$

**Why it matters:** Without absolute value, the antiderivative is undefined for $x < 0$.

------

**2. Sign errors in integration by parts**

❌ Common mistake: $\int u\,dv = uv + \int v\,du$

✓ Correct: $\int u\,dv = uv - \int v\,du$

------

**3. Bad choice of $u$ and $dv$ in IBP**

**LIATE Rule for choosing $u$（对反幂三指）:**

- **L**ogarithmic
- **I**nverse trigonometric
- **A**lgebraic (polynomials)
- **T**rigonometric
- **E**xponential

Choose $u$ based on what appears first in this list.

**Example:** For $\int x e^x dx$:

- $x$ is algebraic (A)
- $e^x$ is exponential (E)
- Choose $u = x$, $dv = e^x dx$ ✓

------

**4. Not simplifying before integrating**

❌ Attempting: $\int \frac{x^2-1}{x-1}dx$ directly

✓ Simplify first: $\frac{x^2-1}{x-1} = \frac{(x-1)(x+1)}{x-1} = x+1$ (for $x \neq 1$)

Then: $\int (x+1)dx = \frac{x^2}{2} + x + C$

------

**5. Boundary term errors in definite integrals**

When using IBP on definite integrals, **always evaluate the boundary term** $[uv]_a^b$.

❌ Common error: Forgetting to evaluate at both limits

✓ Careful: $\int_a^b u,dv = [uv]_a^b - \int_a^b v,du$

------

**6. Incorrect trigonometric identities**

- $\sin^2 x + \cos^2 x = 1$ ✓
- $1 + \tan^2 x = \sec^2 x$ ✓
- $1 + \cot^2 x = \csc^2 x$ ✓

------

**7. Forgetting to back-substitute**

After substitution, **always convert back to the original variable**.

Example: After $u = \sin x$: $\int \sin^2 x \cos x \, dx = \int u^2\,du = \frac{u^3}{3} + C$

❌ Leaving as $\frac{u^3}{3} + C$

✓ Complete: $\frac{\sin^3 x}{3} + C$

------

**8. Domain issues with inverse trigonometric functions**

- $\arcsin x$ and $\arccos x$: domain $[-1, 1]$
- $\arctan x$ and $\text{arccot } x$: domain $(-\infty, \infty)$
- $\text{arcsec } x$ and $\text{arccsc } x$: domain $(-\infty, -1] \cup [1, \infty)$

Always check that expressions remain in valid domains.

------

**9. Incorrect substitution of differentials**

❌ Common error: $\int \cos(2x)dx = \sin(2x) + C$

✓ Correct: Use substitution $u = 2x$, $du = 2dx$ ⇒ $dx = \frac{du}{2}$
$\int \cos(2x)dx = \int \cos(u)\cdot\frac{du}{2} = \frac{1}{2}\sin u + C = \frac{1}{2}\sin(2x) + C$

Always express $du = f(x)\,dx$ explicitly to prevent omission.

------

### 14.3 Efficiency Comparison

| Method                   | Best for                    | Advantages                   | Disadvantages                      |
| ------------------------ | --------------------------- | ---------------------------- | ---------------------------------- |
| **Direct substitution**  | Obvious chain rule forms    | Fast, simple                 | Limited applicability              |
| **IBP**                  | Products, inverse functions | Versatile                    | Can be tedious, sign errors        |
| **Trig substitution**    | $\sqrt{a^2-x^2}$, etc.      | Handles radicals             | Requires careful back-substitution |
| **Partial fractions**    | Rational functions          | Systematic                   | Algebra-intensive                  |
| **Complex exponentials** | High trig powers            | Systematic, powerful         | Requires complex arithmetic        |
| **Reduction formulas**   | Repeated similar integrals  | Reduces power systematically | Recursive, multiple steps          |
| **Weierstrass subst.**   | Rational trig functions     | Universal (always works)     | Often produces messy expressions   |

------

### 14.4 Integration Strategy Principles

**1. Always look before you leap**

- Survey the entire integrand before choosing a method
- Check for simplifications (factoring, cancellation)
- Identify the "type" of integral

**2. Exploit symmetry and special structure**

- For definite integrals, check King property and even/odd
- Look for hidden patterns (product-to-sum, etc.)

**3. Transform to familiar territory**

- Goal: convert unfamiliar integral to known form
- Each substitution should simplify the problem

**4. When stuck, try multiple approaches**

- Don't commit to first method if it's not working
- Sometimes the "wrong" substitution reveals a better path

**5. Verify your answer**

- Differentiate to check indefinite integrals
- Use numerical methods to verify definite integrals
- Check boundary behavior and special cases

**6. Build your intuition**

- Practice recognizing patterns
- Keep a personal "integral library" of solved problems
- Understand why methods work, not just how

公曰：

> 夫积分之巧，非徒术也，实载变通之智。易元转繁为简，如辟径通幽；分部分合相济，若解结理丝；三角化弦为直，似驯曲就方；复数越域求通，犹破壁寻途。四术虽殊，其要一也：以变应变，以简驭繁。
