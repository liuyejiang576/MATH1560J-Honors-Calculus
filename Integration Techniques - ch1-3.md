# Integration Techniques 积佬修炼手册

Yuebo Hu, TA of MATH1560J, GC, SJTU

liuyejiang576@sjtu.edu.cn

October, 2025



## Introduction

Integration is the art of finding the whole from knowledge of its parts. It requires creativity, pattern recognition, and often, a touch of ingenuity that transcends mechanical application. Unlike differentiation, where the chain rule, product rule, and quotient rule provide clear procedures, integration has no universal algorithm. Two integrals that appear similar may require completely different techniques. Success in integration comes from:

1. **Pattern Recognition**: Seeing which technique applies
2. **Strategic Thinking**: Knowing when to transform the problem
3. **Algebraic Flexibility**: Manipulating expressions to reveal structure
4. **Persistence**: Trying multiple approaches when the first doesn't work



------

## Contents

1. Direct Substitution Methods
2. Integration by Parts
3. Trigonometric Power Reduction
4. Secant-Tangent Power Reduction
5. Polynomial $\times$ Exponential
6. Exponential $\times$ Trigonometric
7. Polynomial $\times$ Trigonometric
8. Partial Fractions
9. Common Methods for Definite Integral
10. Comprehensive Definite Integrals
11. Special Functions and Their Integrals
12. Equalities and Inequalities
13. Recognition of Non-Elementary Forms
14. Summary

---



## Part I: Foundational Methods

积分很简单的，至少在这一部分如此。

### 1. Direct Substitution Methods

The substitution rule, also called $u$-substitution or change of variables, states: 

$\int f(g(x))g'(x)dx = \int f(u)du$  where $ u = g(x) $

**How to Choose a Substitution:**

- Look for a function whose derivative appears elsewhere in the integrand
- Identify the "most complicated" part that can be simplified
- Check if the remaining terms can be expressed in terms of the new variable

------

### 1.1 Dericvatve Substitution

**Basic Principle:** When the integrand contains a specific algebraic expression repeatedly or when its derivative is present, substitute that expression.

**Example 1.1.1:** Evaluate $\int \frac{2x+3}{x^2+3x+5}dx$

**Solution:**

Notice that the numerator $2x+3$ is exactly the derivative of the denominator $x^2+3x+5$.

Let $u = x^2+3x+5$

Then $du = (2x+3)dx$

The integral becomes: $$\int \frac{2x+3}{x^2+3x+5}dx = \int \frac{du}{u} = \ln|u| + C = \ln|x^2+3x+5| + C$$

**Verification:** Differentiate the answer: $$\frac{d}{dx}\ln|x^2+3x+5| = \frac{2x+3}{x^2+3x+5}$$ ✓

**Key Pattern:** When you see $\int \frac{f'(x)}{f(x)}dx$, the answer is always $\ln|f(x)| + C$.

------

**Example 1.1.2:** Evaluate $\int \frac{3x^2-2x+1}{x^3-x^2+x-1}dx$

**Solution:**

Check if the numerator is the derivative of the denominator: $$\frac{d}{dx}(x^3-x^2+x-1) = 3x^2-2x+1$$ ✓

Therefore: $$\int \frac{3x^2-2x+1}{x^3-x^2+x-1}dx = \ln|x^3-x^2+x-1| + C$$

**Common Mistake:** Don't forget the absolute value signs in logarithms! The domain of $\ln(x)$ is only $x > 0$, but $\ln|x|$ is defined for all $x \neq 0$.

**Example 1.1.3:** Evaluate $\int \frac{x}{\sqrt{1+x^2}}dx$

**Solution:**

Let $u = \sqrt{1+x^2}$, then $du = \frac{x}{\sqrt{1+x^2}}dx$
Therefore: $$\int \frac{x}{\sqrt{1+x^2}}dx = \int du = u + C = \sqrt{1+x^2} + C$$

**Example 1.1.4:** Evaluate $\displaystyle\int \frac{\sin x}{1+\cos x}dx$

**Solution:**

Let $u = 1+\cos x$, then $du = -\sin x\,dx$:

$$\int \frac{\sin x}{1+\cos x}dx = -\int \frac{du}{u} = -\ln|u| + C = -\ln|1+\cos x| + C$$

------

### 1.2 Exponential Substitution

When the integrand contains an exponential function and its derivative is present (up to a constant factor), use substitution.

**Example 1.2.1:** Evaluate $\int \frac{e^x}{(e^x+1)^2}dx$

**Solution:**
Let $u = e^x + 1$, then $du = e^x dx$:
$$\int \frac{e^x}{(e^x+1)^2}dx = \int \frac{du}{u^2} = -\frac{1}{u} + C = -\frac{1}{e^x + 1} + C$$

---

**Example 1.2.2:** Evaluate $\int \frac{\cosh x \cdot e^x}{(e^{2x} + 2x)}dx$

**Solution:**

Let $u = e^{2x} + 2x$, then $du = (2e^{2x} + 2)dx$:

$$\int \frac{\cosh x \cdot e^x}{(e^{2x} + 2x)}dx = \int \frac{1/4 \, du}{u^2} = -\frac{1}{4u} + C = -\frac{1}{4(e^{2x} + 2x)} + C$$

---

**Example 1.2.3:** Evaluate $\int \operatorname{csch}(x) \ \, dx$

**Solution:**

$$\operatorname{csch}(x) = \frac{1}{\sinh(x)} = \frac{2}{e^x - e^{-x}} = \frac{2e^x}{e^{2x} - 1}$$

Let $u = e^x$, $du = e^x dx$:

$$\int \frac{2e^x}{e^{2x}-1}dx = \int \frac{2}{u^2-1}du$$

Use partial fractions: $\frac{2}{u^2-1} = \frac{2}{(u-1)(u+1)} = \frac{1}{u-1} - \frac{1}{u+1}$:

$$= \int \left[\frac{1}{u-1} - \frac{1}{u+1}\right]du = \ln|u-1| - \ln|u+1| + C$$

$$= \ln\left|\frac{u-1}{u+1}\right| + C = \ln\left|\frac{e^x-1}{e^x+1}\right| + C$$

**Alternative form:**

$$\frac{e^x-1}{e^x+1} = \frac{e^{x/2}(e^{x/2}-e^{-x/2})}{e^{x/2}(e^{x/2}+e^{-x/2})} = \frac{e^{x/2}-e^{-x/2}}{e^{x/2}+e^{-x/2}} = \frac{2\sinh(x/2)}{2\cosh(x/2)} = \tanh(x/2)$$

**Answer:** $\boxed{\ln|\tanh(x/2)| + C}$ or equivalently $\boxed{\ln\left|\frac{e^x-1}{e^x+1}\right| + C}$

------

### 1.3 Power Substitution

When the integrand contains a polynomial expression raised to a power, and the derivative of the inner polynomial is present (up to a constant factor), use substitution.

**Example 1.3.1:** Evaluate $\int \frac{x^3}{(x^2+1)^2}dx$

**Solution:**

Let $u = x^2 + 1$, then $x^2 = u - 1$ and $2x \, dx = du$, so $x \, dx = \frac{du}{2}$

Also, $x^2 = u - 1$: $$\int \frac{x^3}{(x^2+1)^2}dx = \int \frac{x^2 \cdot x \, dx}{(x^2+1)^2}$$

$$= \int \frac{(u-1)}{u^2} \cdot \frac{du}{2} = \frac{1}{2}\int \frac{u-1}{u^2}du$$

$$= \frac{1}{2}\int \left[\frac{1}{u} - \frac{1}{u^2}\right]du$$

$$= \frac{1}{2}\left[\ln|u| + \frac{1}{u}\right] + C$$

$$= \frac{\ln(x^2+1)}{2} + \frac{1}{2(x^2+1)} + C$$

------

**Example 1.3.2:** Evaluate $\int \frac{x^5}{(x^2+4)^2}dx$

**Solution:**

Let $u = x^2 + 4$, then $x^2 = u - 4$ and $x \, dx = \frac{du}{2}$:

$$\int \frac{x^5}{(x^2+4)^2}dx = \int \frac{x^4 \cdot x \, dx}{(x^2+4)^2} = \int \frac{(x^2)^2}{u^2} \cdot \frac{du}{2}$$

$$= \frac{1}{2}\int \frac{(u-4)^2}{u^2}du = \frac{1}{2}\int \frac{u^2 - 8u + 16}{u^2}du$$

$$= \frac{1}{2}\int \left[1 - \frac{8}{u} + \frac{16}{u^2}\right]du$$

$$= \frac{1}{2}\left[u - 8\ln|u| - \frac{16}{u}\right] + C$$

$$= \frac{x^2+4}{2} - 4\ln(x^2+4) - \frac{8}{x^2+4} + C$$

$$= \frac{x^2}{2} + 2 - 4\ln(x^2+4) - \frac{8}{x^2+4} + C$$

Absorbing the constant 2 into $C$:

**Answer:** $\boxed{\frac{x^2}{2} - 4\ln(x^2+4) - \frac{8}{x^2+4} + C}$

------

**Example 1.3.3:** Evaluate $\int \frac{x^7}{(x^2+1)^3}dx$

**Solution:**

Let $u = x^2 + 1$: $$\int \frac{x^7}{(x^2+1)^3}dx = \int \frac{(x^2)^3 \cdot x \, dx}{(x^2+1)^3} = \frac{1}{2}\int \frac{(u-1)^3}{u^3}du$$

Expand $(u-1)^3 = u^3 - 3u^2 + 3u - 1$:

$$= \frac{1}{2}\int \frac{u^3 - 3u^2 + 3u - 1}{u^3}du = \frac{1}{2}\int \left[1 - \frac{3}{u} + \frac{3}{u^2} - \frac{1}{u^3}\right]du$$

$$= \frac{1}{2}\left[u - 3\ln|u| - \frac{3}{u} + \frac{1}{2u^2}\right] + C$$

$$= \frac{x^2+1}{2} - \frac{3\ln(x^2+1)}{2} - \frac{3}{2(x^2+1)} + \frac{1}{4(x^2+1)^2} + C$$

------

### 1.4 Weierstrass (Universal t-) Substitution

It's called "universal" because it can, in principle, convert any rational function of trigonometric functions into a rational function of a single variable.

**The Substitution:** $$t = \tan\frac{x}{2}$$

**The Transformation Formulas:**  $$\sin x = \frac{2t}{1+t^2}, \quad \cos x = \frac{1-t^2}{1+t^2}, \quad dx = \frac{2dt}{1+t^2}$$

From $t = \tan\frac{x}{2}$, we have $\frac{x}{2} = \arctan t$, so $x = 2\arctan t$. Differentiating: $dx = \frac{2dt}{1+t^2}$ ✓

For sine and cosine, use the double-angle formulas: $$\sin x = 2\sin\frac{x}{2}\cos\frac{x}{2}$$

From the right triangle where $\tan\frac{x}{2} = t$:

- Opposite side: $t$
- Adjacent side: $1$
- Hypotenuse: $\sqrt{1+t^2}$

Therefore: $$\sin\frac{x}{2} = \frac{t}{\sqrt{1+t^2}}, \quad \cos\frac{x}{2} = \frac{1}{\sqrt{1+t^2}}$$

$$\sin x = 2\sin\frac{x}{2}\cos\frac{x}{2} = 2 \cdot \frac{t}{\sqrt{1+t^2}} \cdot \frac{1}{\sqrt{1+t^2}} = \frac{2t}{1+t^2}$$ ✓

$$\cos x = \cos^2\frac{x}{2} - \sin^2\frac{x}{2} = \frac{1}{1+t^2} - \frac{t^2}{1+t^2} = \frac{1-t^2}{1+t^2}$$ ✓

------

**Example 1.4.1:** Evaluate $\int \frac{dx}{1+\sin x + \cos x}$

**Solution:**

Let $t = \tan\frac{x}{2}$

Then: $$\sin x = \frac{2t}{1+t^2}, \quad \cos x = \frac{1-t^2}{1+t^2}, \quad dx = \frac{2dt}{1+t^2}$$

Substitute: $$\int \frac{dx}{1+\sin x + \cos x} = \int \frac{\frac{2dt}{1+t^2}}{1 + \frac{2t}{1+t^2} + \frac{1-t^2}{1+t^2}}$$

Simplify the denominator: $$1 + \frac{2t}{1+t^2} + \frac{1-t^2}{1+t^2} = \frac{(1+t^2) + 2t + (1-t^2)}{1+t^2} = \frac{2 + 2t}{1+t^2} = \frac{2(1+t)}{1+t^2}$$

Therefore: $$\int \frac{\frac{2dt}{1+t^2}}{\frac{2(1+t)}{1+t^2}} = \int \frac{2dt}{2(1+t)} = \int \frac{dt}{1+t}$$

------

**Example 1.4.2:** Evaluate $\int \frac{dx}{5+3\cos x}$

**Solution:**

Let $t = \tan\frac{x}{2}$

$$\int \frac{dx}{5+3\cos x} = \int \frac{\frac{2dt}{1+t^2}}{5 + 3 \cdot \frac{1-t^2}{1+t^2}}$$

Simplify the denominator: $$5 + 3 \cdot \frac{1-t^2}{1+t^2} = \frac{5(1+t^2) + 3(1-t^2)}{1+t^2} = \frac{5 + 5t^2 + 3 - 3t^2}{1+t^2} = \frac{8 + 2t^2}{1+t^2}$$

Therefore: $$\int \frac{\frac{2dt}{1+t^2}}{\frac{8+2t^2}{1+t^2}} = \int \frac{2dt}{8+2t^2} = \int \frac{dt}{4+t^2}$$

This is a standard arctangent form: $$\int \frac{dt}{4+t^2} = \frac{1}{2}\arctan\frac{t}{2} + C$$

Substitute back: $$= \frac{1}{2}\arctan\left(\frac{\tan(x/2)}{2}\right) + C$$

------

**Complex Alternative: Contour Integration Preview**

For those familiar with complex analysis, there's an elegant alternative using the substitution $z = e^{ix}$ on the unit circle:

$$\cos x = \frac{z + z^{-1}}{2}, \quad dx = \frac{dz}{iz}$$

For definite integrals over $[0, 2\pi]$, this transforms the problem into a contour integral around the unit circle in the complex plane. While this is beyond our current scope, it's worth noting that the Weierstrass substitution is essentially the "real version" of this complex technique.

------

### 1.5 Rationalizing Radicals

When an integrand contains multiple radicals with different roots, we can often rationalize by substituting the LCD (least common denominator) of the root indices.

If you have $\sqrt{x}$ and $\sqrt[3]{x}$, use $t^6 = x$ (since $\text{lcm}(2,3) = 6$)

- If you have $\sqrt[3]{f(x)}$ and $\sqrt[4]{f(x)}$, use $t^{12} = f(x)$
- After substitution, you'll get a rational function of $t$

------

**Example 1.5.1:** Evaluate $\int \frac{dx}{\sqrt{1-x} + \sqrt[3]{1-x}}$

**Solution:**

We have radicals with indices 2 and 3. The LCM is 6.

Let $t^6 = 1-x$

Then $x = 1-t^6$ and $dx = -6t^5 dt$

Also: $$\sqrt{1-x} = (t^6)^{1/2} = t^3$$ $$\sqrt[3]{1-x} = (t^6)^{1/3} = t^2$$

Substitute: $$\int \frac{dx}{\sqrt{1-x} + \sqrt[3]{1-x}} = \int \frac{-6t^5 dt}{t^3 + t^2}$$

$$= -6\int \frac{t^5}{t^2(t+1)}dt = -6\int \frac{t^3}{t+1}dt$$

Now perform polynomial long division: $$\frac{t^3}{t+1} = t^2 - t + 1 - \frac{1}{t+1}$$

Integrate: $$-6\int \left(t^2 - t + 1 - \frac{1}{t+1}\right)dt$$

$$= -6\left(\frac{t^3}{3} - \frac{t^2}{2} + t - \ln|t+1|\right) + C$$

$$= -2t^3 + 3t^2 - 6t + 6\ln|t+1| + C$$

Substitute back $t = (1-x)^{1/6}$:

$$= -2\sqrt{1-x} + 3\sqrt[3]{1-x} - 6(1-x)^{1/6} + 6\ln\left|(1-x)^{1/6}+1\right| + C$$

This looks complicated, but we can verify by differentiating.

------

**Example 1.5.2:** Evaluate $\int \frac{dx}{\sqrt{x} + \sqrt[3]{x}}$

**Solution:**

Here we have $x^{1/2}$ and $x^{1/3}$, so $\text{lcm}(2,3) = 6$.

Let $t = x^{1/6}$, so $x = t^6$ and $dx = 6t^5 dt$

Then: $$\sqrt{x} = t^3, \quad \sqrt[3]{x} = t^2$$

$$\int \frac{dx}{\sqrt{x} + \sqrt[3]{x}} = \int \frac{6t^5 dt}{t^3 + t^2} = 6\int \frac{t^5}{t^2(t+1)}dt$$

$$= 6\int \frac{t^3}{t+1}dt$$

Using the same long division as before: $$= 6\int \left(t^2 - t + 1 - \frac{1}{t+1}\right)dt$$

$$= 6\left(\frac{t^3}{3} - \frac{t^2}{2} + t - \ln|t+1|\right) + C$$

$$= 2t^3 - 3t^2 + 6t - 6\ln|t+1| + C$$

Substitute $t = x^{1/6}$:

$$= 2\sqrt{x} - 3\sqrt[3]{x} + 6\sqrt[6]{x} - 6\ln|x^{1/6}+1| + C$$

------

**Example 1.5.3:** Evaluate $\int \frac{\sqrt{x}dx}{1+\sqrt[3]{x}}$

**Solution:**

Let $t = x^{1/6}$, then $x = t^6$, $dx = 6t^5 dt$

$$\sqrt{x} = t^3, \quad \sqrt[3]{x} = t^2$$

$$\int \frac{\sqrt{x}dx}{1+\sqrt[3]{x}} = \int \frac{t^3 \cdot 6t^5 dt}{1+t^2} = 6\int \frac{t^8}{1+t^2}dt$$

Polynomial division of $\frac{t^8}{1+t^2}$:

$$t^8 = (1+t^2)(t^6 - t^4 + t^2 - 1) + 1$$

So: $\frac{t^8}{1+t^2} = t^6 - t^4 + t^2 - 1 + \frac{1}{1+t^2}$

$$6\int \left(t^6 - t^4 + t^2 - 1 + \frac{1}{1+t^2}\right)dt$$

$$= 6\left(\frac{t^7}{7} - \frac{t^5}{5} + \frac{t^3}{3} - t + \arctan t\right) + C$$

Substitute back $t = x^{1/6}$:

$$= 6\left(\frac{x^{7/6}}{7} - \frac{x^{5/6}}{5} + \frac{x^{1/2}}{3} - x^{1/6} + \arctan(x^{1/6})\right) + C$$

------

### 1.6 Quadratic Expressions

Integrals involving $\sqrt{ax^2 + bx + c}$ can often be simplified by first completing the square, then applying a trigonometric substitution.

**The Three Standard Trigonometric Substitutions:**

1. **For $\sqrt{a^2 - x^2}$:** Use $x = a\sin\theta$
   - Then $\sqrt{a^2-x^2} = a\cos\theta$
   - Range: $\theta \in [-\pi/2, \pi/2]$
2. **For $\sqrt{x^2 + a^2}$:** Use $x = a\tan\theta$
   - Then $\sqrt{x^2+a^2} = a\sec\theta$
   - Range: $\theta \in (-\pi/2, \pi/2)$
3. **For $\sqrt{x^2 - a^2}$:** Use $x = a\sec\theta$
   - Then $\sqrt{x^2-a^2} = a\tan\theta$
   - Range: $\theta \in [0, \pi/2) \cup (\pi/2, \pi]$

Each substitution uses a Pythagorean identity:

- $\sin^2\theta + \cos^2\theta = 1$
- $1 + \tan^2\theta = \sec^2\theta$
- $\sec^2\theta - 1 = \tan^2\theta$

------

**Example 1.6.1:** Evaluate $\int \frac{dx}{\sqrt{8x-x^2}}$

**Solution:**

**Step 1: Complete the Square**

$$8x - x^2 = -(x^2 - 8x) = -(x^2 - 8x + 16 - 16) = -(x-4)^2 + 16 = 16 - (x-4)^2$$

So: $$\int \frac{dx}{\sqrt{8x-x^2}} = \int \frac{dx}{\sqrt{16-(x-4)^2}}$$

**Step 2: Substitution**

Let $u = x - 4$, then $du = dx$

$$= \int \frac{du}{\sqrt{16-u^2}}$$

This is the form $\sqrt{a^2 - u^2}$ with $a = 4$.

**Step 3: Trigonometric Substitution**

Let $u = 4\sin\theta$, then $du = 4\cos\theta, d\theta$

$$\sqrt{16-u^2} = \sqrt{16-16\sin^2\theta} = \sqrt{16(1-\sin^2\theta)} = 4\cos\theta$$

(We take the positive root since $\cos\theta \geq 0$ for $\theta \in [-\pi/2, \pi/2]$)

$$\int \frac{4\cos\theta\, d\theta}{4\cos\theta} = \int d\theta = \theta + C$$

**Step 4: Back-Substitution**

From $u = 4\sin\theta$, we have $\sin\theta = \frac{u}{4}$

Therefore $\theta = \arcsin\frac{u}{4} = \arcsin\frac{x-4}{4}$

**Answer:** $\boxed{\arcsin\left(\frac{x-4}{4}\right) + C}$

**Verification:** $$\frac{d}{dx}\arcsin\left(\frac{x-4}{4}\right) = \frac{1}{\sqrt{1-\left(\frac{x-4}{4}\right)^2}} \cdot \frac{1}{4} = \frac{1}{\sqrt{16-(x-4)^2}} = \frac{1}{\sqrt{8x-x^2}}$$ ✓

------

**Example 1.6.2:** Evaluate $\int \frac{dx}{\sqrt{x^2+6x+13}}$

**Solution:**

**Step 1: Complete the Square**

$$x^2 + 6x + 13 = (x^2 + 6x + 9) + 4 = (x+3)^2 + 4$$

$$\int \frac{dx}{\sqrt{x^2+6x+13}} = \int \frac{dx}{\sqrt{(x+3)^2+4}}$$

**Step 2: Substitution**

Let $u = x+3$, then $du = dx$

$$= \int \frac{du}{\sqrt{u^2+4}}$$

This is the form $\sqrt{u^2 + a^2}$ with $a = 2$.

**Step 3: Trigonometric Substitution**

Let $u = 2\tan\theta$, then $du = 2\sec^2\theta\, d\theta$

$$\sqrt{u^2+4} = \sqrt{4\tan^2\theta + 4} = 2\sqrt{\tan^2\theta+1} = 2\sec\theta$$

$$\int \frac{2\sec^2\theta\, d\theta}{2\sec\theta} = \int \sec\theta\, d\theta$$

**Recall:** $\int \sec\theta\, d\theta = \ln|\sec\theta + \tan\theta| + C$

**Step 4: Back-Substitution**

From $u = 2\tan\theta$, we have $\tan\theta = \frac{u}{2}$

From a right triangle: $\sec\theta = \frac{\sqrt{u^2+4}}{2}$

$$\ln\left|\frac{\sqrt{u^2+4}}{2} + \frac{u}{2}\right| + C = \ln|\sqrt{u^2+4}+u| - \ln 2 + C$$

Since $-\ln 2$ is just a constant, we can absorb it into $C$:

$$= \ln|\sqrt{u^2+4}+u| + C$$

Substitute $u = x+3$:

$$= \ln\left|\sqrt{x^2+6x+13} + x + 3\right| + C$$

**Alternative Form Using Inverse Hyperbolic:**

Note that $\ln(\sqrt{u^2+4}+u) = \operatorname{arsinh}(u/2)$

So the answer can also be written as: $$\operatorname{arsinh}\left(\frac{x+3}{2}\right) + C$$

------

**Example 1.6.3:** Evaluate $\int \sqrt{4x-x^2} \, dx$

**Solution:**

**Step 1: Complete the Square**

$$4x - x^2 = -(x^2-4x) = -(x^2-4x+4-4) = -(x-2)^2 + 4 = 4-(x-2)^2$$

$$\int \sqrt{4x-x^2} \, dx = \int \sqrt{4-(x-2)^2} \, dx$$

**Step 2: Substitution**

Let $u = x-2$, then $du = dx$

$$= \int \sqrt{4-u^2}\, du$$

**Step 3: Trigonometric Substitution**

Let $u = 2\sin\theta$, then $du = 2\cos\theta\, d\theta$

$$\sqrt{4-u^2} = 2\cos\theta$$

$$\int 2\cos\theta \cdot 2\cos\theta\, d\theta = 4\int \cos^2\theta\, d\theta$$

Use the identity: $\cos^2\theta = \frac{1+\cos 2\theta}{2}$

$$= 4\int \frac{1+\cos 2\theta}{2}d\theta = 2\int (1+\cos 2\theta)d\theta$$

$$= 2\left(\theta + \frac{\sin 2\theta}{2}\right) + C = 2\theta + \sin 2\theta + C$$

$$= 2\theta + 2\sin\theta\cos\theta + C$$

**Step 4: Back-Substitution**

From $u = 2\sin\theta$: $\sin\theta = \frac{u}{2}$, $\theta = \arcsin\frac{u}{2}$

$\cos\theta = \sqrt{1-\sin^2\theta} = \sqrt{1-\frac{u^2}{4}} = \frac{\sqrt{4-u^2}}{2}$

$$= 2\arcsin\frac{u}{2} + 2 \cdot \frac{u}{2} \cdot \frac{\sqrt{4-u^2}}{2} + C$$

$$= 2\arcsin\frac{u}{2} + \frac{u\sqrt{4-u^2}}{2} + C$$

Substitute $u = x-2$:

$$= 2\arcsin\frac{x-2}{2} + \frac{(x-2)\sqrt{4x-x^2}}{2} + C$$

This integral represents the area under the curve $y = \sqrt{4x-x^2}$, which is a semicircle of radius 2 centered at $(2,0)$. The answer combines an angular part ($\arcsin$) and a triangular part, reflecting the geometry of circular sectors.

------

**Example 1.6.4:** Evaluate $\int \frac{x^2dx}{\sqrt{9-x^2}}$

**Solution:**

This is the form $\sqrt{a^2-x^2}$ with $a = 3$.

Let $x = 3\sin\theta$, then $dx = 3\cos\theta\, d\theta$

$$\sqrt{9-x^2} = 3\cos\theta$$

$$\int \frac{(3\sin\theta)^2 \cdot 3\cos\theta\, d\theta}{3\cos\theta} = \int 9\sin^2\theta\, d\theta$$

Use $\sin^2\theta = \frac{1-\cos 2\theta}{2}$:

$$= 9\int \frac{1-\cos 2\theta}{2}d\theta = \frac{9}{2}\left(\theta - \frac{\sin 2\theta}{2}\right) + C$$

$$= \frac{9\theta}{2} - \frac{9\sin 2\theta}{4} + C$$

Use $\sin 2\theta = 2\sin\theta\cos\theta$:

$$= \frac{9\theta}{2} - \frac{9\sin\theta\cos\theta}{2} + C$$

**Back-substitution:**

From $x = 3\sin\theta$: $\sin\theta = \frac{x}{3}$, $\theta = \arcsin\frac{x}{3}$

$\cos\theta = \frac{\sqrt{9-x^2}}{3}$

$$= \frac{9}{2}\arcsin\frac{x}{3} - \frac{9}{2} \cdot \frac{x}{3} \cdot \frac{\sqrt{9-x^2}}{3} + C$$

$$= \frac{9}{2}\arcsin\frac{x}{3} - \frac{x\sqrt{9-x^2}}{2} + C$$

---

### 1.7 Conjugate Methods

When an integrand contains sums or differences involving radicals or trigonometric expressions, multiplying by a conjugate can sometimes rationalize the expression and reveal a simpler structure.

**Basic Principle:** For expressions of the form $a + b$ or $a - b$, multiply numerator and denominator by the conjugate $a - b$ or $a + b$ respectively, using the algebraic identity: $$(a+b)(a-b) = a^2 - b^2$$

This is particularly useful when:

- Radicals appear in sums or differences ($\sqrt{A} \pm \sqrt{B}$)
- The resulting difference of squares simplifies the problem
- Direct substitution is not immediately apparent

------

**Example 1.7.1:** Evaluate $\displaystyle\int \frac{x\,dx}{\sqrt{x}-\sqrt{x-1}}$

**Solution:**

Multiply by the conjugate $\sqrt{x}+\sqrt{x-1}$:

$$\int \frac{x\,dx}{\sqrt{x}-\sqrt{x-1}} = \int \frac{x(\sqrt{x}+\sqrt{x-1})dx}{(\sqrt{x}-\sqrt{x-1})(\sqrt{x}+\sqrt{x-1})}$$

$$= \int \frac{x(\sqrt{x}+\sqrt{x-1})dx}{x-(x-1)} = \int x(\sqrt{x}+\sqrt{x-1})dx$$

$$= \int (x^{3/2} + x\sqrt{x-1})dx$$

For the first term: $$\int x^{3/2}dx = \frac{2x^{5/2}}{5}$$

For the second term, let $u = x-1$, then $x = u+1$ and $dx = du$: $$\int x\sqrt{x-1}\,dx = \int (u+1)\sqrt{u}\,du = \int (u^{3/2} + u^{1/2})du$$

$$= \frac{2u^{5/2}}{5} + \frac{2u^{3/2}}{3} = \frac{2(x-1)^{5/2}}{5} + \frac{2(x-1)^{3/2}}{3}$$

---

**Example 1.7.2:** Evaluate $\displaystyle\int \frac{dx}{1+\sqrt{x+1}}$

**Solution:**

Multiply by the conjugate $1-\sqrt{x+1}$:

$$\int \frac{dx}{1+\sqrt{x+1}} = \int \frac{dx \cdot (1-\sqrt{x+1})}{(1+\sqrt{x+1})(1-\sqrt{x+1})}$$

$$= \int \frac{(1-\sqrt{x+1})dx}{1-(x+1)} = \int \frac{(1-\sqrt{x+1})dx}{-x}$$

$$= \int \frac{\sqrt{x+1}-1}{x}dx = \int \frac{\sqrt{x+1}}{x}dx - \int \frac{dx}{x}$$

The second integral is $\ln|x|$. For the first, let $u = x+1$, so $x = u-1$ and $dx = du$:

$$\int \frac{\sqrt{x+1}}{x}dx = \int \frac{\sqrt{u}}{u-1}du$$

Let $t = \sqrt{u}$, then $u = t^2$ and $du = 2t\,dt$:

$$= \int \frac{t \cdot 2t\,dt}{t^2-1} = 2\int \frac{t^2}{t^2-1}dt$$

$$= 2\int \left(1 + \frac{1}{t^2-1}\right)dt = 2\int dt + 2\int \frac{dt}{t^2-1}$$

Using partial fractions on $\frac{1}{t^2-1} = \frac{1}{(t-1)(t+1)} = \frac{1/2}{t-1} - \frac{1/2}{t+1}$:

$$= 2t + 2 \cdot \frac{1}{2}\ln\left|\frac{t-1}{t+1}\right| + C = 2t + \ln\left|\frac{t-1}{t+1}\right| + C$$

Back-substitute $t = \sqrt{x+1}$:

$$= 2\sqrt{x+1} + \ln\left|\frac{\sqrt{x+1}-1}{\sqrt{x+1}+1}\right| - \ln|x| + C$$

------

Conjugate multiplication is also useful when dealing with sums and differences of trigonometric functions.

**Example 1.7.3:** Evaluate $\displaystyle\int \frac{dx}{1-\cos x}$

**Solution:**

Multiply by the conjugate $1+\cos x$:

$$\int \frac{dx}{1-\cos x} = \int \frac{(1+\cos x)dx}{(1-\cos x)(1+\cos x)} = \int \frac{(1+\cos x)dx}{1-\cos^2 x}$$

$$= \int \frac{(1+\cos x)dx}{\sin^2 x}$$

Split the integral: $$= \int \frac{dx}{\sin^2 x} + \int \frac{\cos x\,dx}{\sin^2 x}$$

$$= \int \csc^2 x\,dx + \int \frac{\cos x}{\sin^2 x}dx$$

The first integral: $\int \csc^2 \,dx = -\cot x + C$

For the second, let $u = \sin x$, $du = \cos x\,dx$: $$\int \frac{\cos x}{\sin^2 x}dx = \int \frac{du}{u^2} = -\frac{1}{u} = -\frac{1}{\sin x} = -\csc x$$

**Answer:** $$\boxed{-\cot x - \csc x + C}$$

**Alternative form:** This can also be written as $-\cot x - \csc x = -\frac{\cos x + 1}{\sin x} + C$

------

**Example 1.7.4:** Evaluate $\displaystyle\int \frac{dx}{1+\sin x}$

**Solution:**

Multiply by the conjugate $1-\sin x$:

$$\int \frac{dx}{1+\sin x} = \int \frac{(1-\sin x)dx}{(1+\sin x)(1-\sin x)} = \int \frac{(1-\sin x)dx}{1-\sin^2 x}$$

$$= \int \frac{(1-\sin x)dx}{\cos^2 x}$$

Split the integral: $$= \int \frac{dx}{\cos^2 x} - \int \frac{\sin x\,dx}{\cos^2 x}$$

$$= \int \sec^2 x\,dx - \int \frac{\sin x}{\cos^2 x}dx$$

The first integral: $\int \sec^2 x\,dx = \tan x + C$

For the second, let $u = \cos x$, $du = -\sin x\,dx$: $$\int \frac{\sin x}{\cos^2 x}dx = -\int \frac{du}{u^2} = \frac{1}{u} = \frac{1}{\cos x} = \sec x$$

**Answer:** $$\boxed{\tan x - \sec x + C}$$

------

**When to use conjugate multiplication:**

- Sums or differences of radicals in the denominator
- $1 \pm \sin x$ or $1 \pm \cos x$ in the denominator
- When simpler methods (like direct substitution) aren't obvious

---

### 1.8 Ansatz Methods

“Ansatz” means “educated guess”. Sometimes integration requires **reverse engineering**. When we look at an integrand and can imagine what its antiderivative might look like, we can propose a trial solution with undetermined coefficients, then differentiate to find those coefficients.

**When to Use Ansatz:**

- The form of the derivative suggests what the antiderivative looks like
- You see patterns like "function × its derivative" but with extra terms
- The integrand combines simple functions (logs, polynomials, exponentials)
- Straightforward substitution doesn't quite work, but the structure is recognizable

Consider $\int \frac{\ln x}{x^3}dx$. This doesn't fit our standard substitution patterns. The derivative of $\ln x$ is $\frac{1}{x}$, but that doesn't immediately help. Let's think backwards: **what kind of function, when differentiated, produces $\frac{\ln x}{x^3}$?**

**Building the Ansatz:**

If we differentiate $\frac{\ln x}{x^2}$, we get: $$\frac{d}{dx}\left(\frac{\ln x}{x^2}\right) = \frac{\frac{1}{x} \cdot x^2 - \ln x \cdot 2x}{x^4} = \frac{x - 2x\ln x}{x^4} = \frac{1 - 2\ln x}{x^3}$$

We got $\frac{1}{x^3}$ and $\frac{\ln x}{x^3}$ terms—exactly the structure we need! But the coefficients are wrong. This suggests our ansatz should have the form: $$F(x) = \frac{a + b\ln x}{x^2}$$

where $a$ and $b$ are constants to be determined.

**Why this form?**

- **Why $\frac{1}{x^2}$ in the denominator?** Because we have $\frac{1}{x^3}$ in the integrand. When we differentiate using the quotient rule, we'll get $x^4$ in the denominator, which simplifies back to $x^3$.
- **Why $a + b\ln x$ in the numerator?** Because differentiating $\ln x$ gives a constant term ($\frac{1}{x}$), and differentiating a constant gives zero. We need both to balance the equation.
- **Why not $\frac{a + b\ln x}{x}$?** This would give us denominators with lower powers of $x$, not $x^3$.
- **Why not additional terms like $cx$?** Keep it minimal—add complexity only if needed.

------

**Example 1.8.1:** Evaluate $\int \frac{\ln x}{x^3}dx$

**Solution:**

Propose the ansatz: $$F(x) = \frac{a + b\ln x}{x^2}$$

$$F'(x) = \frac{\frac{b}{x} \cdot x^2 - (a + b\ln x) \cdot 2x}{x^4} = \frac{-2a + b - 2b\ln x}{x^3}$$

We want this to equal $\frac{\ln x}{x^3}$. Matching coefficients:

$b = -\frac{1}{2}$,  $a = -\frac{1}{4}$

$$\boxed{\int \frac{\ln x}{x^3}dx = -\frac{1 + 2\ln x}{4x^2} + C}$$

------

**Example 1.8.3:** Evaluate $\int \frac{(\ln x)^2}{x^3}dx$

**Solution:**

Now we have $(\ln x)^2$ instead of $\ln x$. What happens when we differentiate $(\ln x)^2$?

$$\frac{d}{dx}[(\ln x)^2] = 2\ln x \cdot \frac{1}{x} = \frac{2\ln x}{x}$$

This produces a $\ln x$ term. So our ansatz needs $(\ln x)^2$ and $\ln x$ terms:

Let $F(x) = \frac{a + b\ln x + c(\ln x)^2}{x^2}$

Differentiate: $$F'(x) = \frac{\left[\frac{b}{x} + \frac{2c\ln x}{x}\right] \cdot x^2 - [a + b\ln x + c(\ln x)^2] \cdot 2x}{x^4}$$

$$= \frac{(b - 2a) + (2c - 2b)\ln x - 2c(\ln x)^2}{x^3}$$

Match with $\frac{(\ln x)^2}{x^3}$:

$c = -\frac{1}{2}$,  $b = -\frac{1}{2}$,  $a = -\frac{1}{4}$

 $$\boxed{\int \frac{(\ln x)^2}{x^3}dx = -\frac{1 + 2\ln x + 2(\ln x)^2}{4x^2} + C}$$

------

**Example 1.8.3:** Evaluate $\int \frac{dx}{ae^x + b}$ where $a, b$ are constants

**Solution:**

**Approach 1: Multiply by $\frac{e^{-x}}{e^{-x}}$**

$$\int \frac{dx}{ae^x + b} = \int \frac{e^{-x}dx}{a + be^{-x}}$$

Now let $u = a + be^{-x}$, then $du = -be^{-x}dx$, so $e^{-x}dx = -\frac{du}{b}$

$$= \int \frac{-\frac{du}{b}}{u} = -\frac{1}{b}\ln|u| + C = -\frac{1}{b}\ln|a + be^{-x}| + C$$

We can simplify further: $$-\frac{1}{b}\ln|a + be^{-x}| = -\frac{1}{b}\ln\left|\frac{ae^x + b}{e^x}\right| = -\frac{1}{b}[\ln|ae^x + b| - x]$$

$$\boxed{\int \frac{dx}{ae^x + b} = \frac{x}{b} - \frac{1}{b}\ln|ae^x + b| + C}$$

**Approach 2: Ansatz Thinking**

Could we have guessed this form? Notice that:

- Exponentials in the denominator suggest logs
- But we also have a linear $x$ term

If we tried $F(x) = Ax + B\ln(ae^x + b)$, then: $$F'(x) = A + B \cdot \frac{ae^x}{ae^x + b}$$

For this to equal $\frac{1}{ae^x + b}$, we need: $$A + \frac{Bae^x}{ae^x + b} = \frac{1}{ae^x + b}$$

Multiply through by $ae^x + b$: $$A(ae^x + b) + Bae^x = 1$$

$$Aae^x + Ab + Bae^x = 1$$

$$(Aa + Ba)e^x + Ab = 1$$

This must hold for all $x$, so:

- Coefficient of $e^x$: $Aa + Ba = 0$
- Constant term: $Ab = 1$

From the second equation: $A = \frac{1}{b}$

From the first: $\frac{a}{b} + Ba = 0$, so $B = -\frac{1}{b}$

This confirms: $F(x) = \frac{x}{b} - \frac{1}{b}\ln|ae^x + b| + C$ ✓

------

**Example 1.8.4:** Evaluate $\int (3x - 5)e^{2x} dx$

**Solution:**

With $e^{2x}$, differentiation brings down a factor of 2.

Let $F(x) = (ax + b)e^{2x}$

$$F'(x) = a \cdot e^{2x} + (ax + b) \cdot 2e^{2x} = [a + 2ax + 2b]e^{2x} = [2ax + (a + 2b)]e^{2x}$$

Match with $(3x - 5)e^{2x}$:

- Coefficient of $x$: $2a = 3$, so $a = \frac{3}{2}$
- Constant: $a + 2b = -5$, so $\frac{3}{2} + 2b = -5$, giving $b = -\frac{13}{4}$

**Answer:** $$\boxed{\int (3x - 5)e^{2x} dx = \left(\frac{3x}{2} - \frac{13}{4}\right)e^{2x} + C}$$

------

**Example 1.8.5:** Evaluate $\int x^2 e^x dx$

**Solution:**

For a quadratic polynomial, try $F(x) = (ax^2 + bx + c)e^x$

Differentiate: $$F'(x) = (2ax + b)e^x + (ax^2 + bx + c)e^x = [ax^2 + (2a + b)x + (b + c)]e^x$$

Match with $x^2 e^x$:

- Coefficient of $x^2$: $a = 1$
- Coefficient of $x$: $2a + b = 0$, so $2 + b = 0$, giving $b = -2$
- Constant: $b + c = 0$, so $-2 + c = 0$, giving $c = 2$

**Answer:** $$\boxed{\int x^2 e^x dx = (x^2 - 2x + 2)e^x + C}$$

**Pattern:** Notice that each differentiation reduces the degree by 1 but adds a lower-degree term. This is why ansatz works for low-degree polynomials but becomes tedious for higher degrees.

------

**Example 1.8.6:** Evaluate $\int (x^2 + 3x - 1)e^{-x} dx$

**Solution:**

Let $F(x) = (ax^2 + bx + c)e^{-x}$

$$F'(x) = (2ax + b)e^{-x} + (ax^2 + bx + c) \cdot (-e^{-x})$$

$$= [(2ax + b) - (ax^2 + bx + c)]e^{-x}$$

$$= [-ax^2 + (2a - b)x + (b - c)]e^{-x}$$

Match with $(x^2 + 3x - 1)e^{-x}$:

- Coefficient of $x^2$: $-a = 1$, so $a = -1$
- Coefficient of $x$: $2a - b = 3$, so $-2 - b = 3$, giving $b = -5$
- Constant: $b - c = -1$, so $-5 - c = -1$, giving $c = -4$

**Answer:** $$\boxed{\int (x^2 + 3x - 1)e^{-x} dx = (-x^2 - 5x - 4)e^{-x} + C}$$

**Note:** With negative exponents, signs alternate in a different pattern. Always check your algebra carefully.



---

### 2. Integration by Parts

Integration by parts is the integral version of the product rule for differentiation. If $(uv)' = u'v + uv'$, then integrating both sides:

$$\int (uv)'dx = \int u'v \, dx + \int uv' \, dx$$

$$uv = \int u'v \, dx + \int uv' \, dx$$

Rearranging: $$\boxed{\int u \, dv = uv - \int v \, du}$$

**The Art of Choosing $u$ and $dv$:**

The success of integration by parts depends critically on choosing which part is $u$ and which is $dv$. A useful mnemonic is **LIATE**（对反幂三指）:

- **L**ogarithmic functions
- **I**nverse trigonometric functions
- **A**lgebraic (polynomial) functions
- **T**rigonometric functions
- **E**xponential functions

Choose $u$ to be the function that appears earliest in this list. The remaining part becomes $dv$.

**Why LIATE Works:**

- Logarithmic and inverse trig functions become simpler when differentiated
- Polynomials reduce degree when differentiated
- Trig and exponential functions don't simplify much, but are easy to integrate

------

### 2.1 Inverse Functions: $\int f^{-1}(x)dx$

**Theoretical Framework:**

To integrate an inverse function, we transform it into a problem involving the original function.

**The Method:**

Let $y = f^{-1}(x)$. Then $x = f(y)$.

Differentiating both sides with respect to $y$: $\frac{dx}{dy} = f'(y)$

Therefore: $dx = f'(y)dy$

The integral becomes: $$\int f^{-1}(x)dx = \int y \cdot f'(y)dy$$

Now apply integration by parts with $u = y$ and $dv = f'(y)dy$:

- $du = dy$
- $v = f(y)$

$$\int y \cdot f'(y)dy = y \cdot f(y) - \int f(y)dy$$

**The General Formula:** $$\int f^{-1}(x)dx = x \cdot f^{-1}(x) - \int f(f^{-1}(x))d(f^{-1}(x))$$

Or more simply, after back-substitution: $$\boxed{\int f^{-1}(x)dx = x \cdot f^{-1}(x) - F(f^{-1}(x)) + C}$$

where $F$ is an antiderivative of $f$.

------

**Example 2.1.1:** Evaluate $\int \arctan x \, dx$

**Solution:**

Here $f^{-1}(x) = \arctan x$, so $f(y) = \tan y$.

**Step 1: Substitution**

Let $y = \arctan x$. Then $x = \tan y$ and $dx = \sec^2 y\, dy$.

$$\int \arctan x \, dx = \int y \cdot \sec^2 y\, dy$$

**Step 2: Integration by Parts**

Let $u = y$ and $dv = \sec^2 y\, dy$

Then $du = dy$,  $v = \int \sec^2 y \, dy = \tan y$

$$\int y \sec^2 y \, dy = y \tan y - \int \tan y \, dy$$

**Step 3: Integrate $\tan y$**

$$\int \tan y \, dy = \int \frac{\sin y}{\cos y}dy = \ln|\sec y| + C$$

**Step 4: Back-substitution**

$$\int y \sec^2 y \, dy = y\tan y - (-\ln|\cos y|) + C = y\tan y + \ln|\cos y| + C$$

From $y = \arctan x$ and $x = \tan y$:

$$= (\arctan x) \cdot x + \ln|\cos(\arctan x)| + C$$

We need to express $\cos(\arctan x)$ in terms of $x$.

From a right triangle where $\tan y = x$: Opposite: $x$, Adjacent: $1$, Hypotenuse: $\sqrt{1+x^2}$

Therefore: $\cos y = \frac{1}{\sqrt{1+x^2}}$

$$= x\arctan x + \ln\left|\frac{1}{\sqrt{1+x^2}}\right| + C$$

$$= x\arctan x + \ln(1+x^2)^{-1/2} + C$$

$\boxed{ = x\arctan x - \frac{1}{2}\ln(1+x^2) + C}$

**Verification:** $$\frac{d}{dx}\left[x\arctan x - \frac{1}{2}\ln(1+x^2)\right] = \arctan x + x \cdot \frac{1}{1+x^2} - \frac{1}{2} \cdot \frac{2x}{1+x^2}$$

$$= \arctan x + \frac{x}{1+x^2} - \frac{x}{1+x^2} = \arctan x$$ ✓

------

### 2.2 Complete Inverse Function Catalog

**Inverse Trigonometric Functions**

**Example 2.2.1:** $\int \arcsin x \, dx$

Let $y = \arcsin x$, so $x = \sin y$ and $dx = \cos y\, dy$

$$\int \arcsin x \, dx = \int y \cos y\, dy$$

Integration by parts: $u = y$, $dv = \cos y \, dy$, $du = dy$, $v = \sin y$

$$= y\sin y - \int \sin y \, dy = y\sin y + \cos y + C$$

Back-substitute: $y = \arcsin x$, $\sin y = x$, $\cos y = \sqrt{1-x^2}$

**Answer:** $\boxed{x\arcsin x + \sqrt{1-x^2} + C}$

------

**Example 2.2.2:** $\int \arccos x \, dx$

Let $y = \arccos x$, so $x = \cos y$ and $dx = -\sin y \, dy$

$$\int \arccos x \, dx = \int y \cdot (-\sin y)dy = -\int y\sin y\, dy$$

Integration by parts: $u = y$, $dv = \sin y \, dy$, $du = dy$, $v = -\cos y$

$$= -(-y\cos y - \int -\cos y\, dy) = -(-y\cos y + \sin y) + C$$

$$= y\cos y - \sin y + C$$

Back-substitute: $y = \arccos x$, $\cos y = x$, $\sin y = \sqrt{1-x^2}$

**Answer:** $\boxed{x\arccos x - \sqrt{1-x^2} + C}$

------

**Example 2.2.3:** $\int \operatorname{arccot} x \, dx$

Let $y = \operatorname{arccot} x$, so $x = \cot y$ and $dx = -\csc^2 y\, dy$

$$\int \operatorname{arccot} x \, dx = \int y \cdot (-\csc^2 y)dy = -\int y\csc^2 y\, dy$$

Integration by parts: $u = y$, $dv = \csc^2 y\, dy$, $du = dy$, $v = -\cot y$

$$= -(-y\cot y - \int -\cot y\, dy) = y\cot y - \int \cot y\, dy$$

$$= y\cot y - \ln|\sin y| + C$$

Back-substitute: $y = \operatorname{arccot} x$, $\cot y = x$

For $\sin(\operatorname{arccot} x)$: from triangle with adjacent $x$, opposite $1$, hypotenuse $\sqrt{1+x^2}$:

$$\sin y = \frac{1}{\sqrt{1+x^2}}$$

$$= x\operatorname{arccot} x - \ln\left|\frac{1}{\sqrt{1+x^2}}\right| + C$$

$$= x\operatorname{arccot} x + \frac{1}{2}\ln(1+x^2) + C$$

**Answer:** $\boxed{x\operatorname{arccot} x + \frac{1}{2}\ln(1+x^2) + C}$

------

**Example 2.2.4:** $\int \operatorname{arcsec} x \, dx$ (for $x \geq 1$)

Let $y = \operatorname{arcsec} x$, so $x = \sec y$ and $dx = \sec y \tan y \, dy$

$$\int \operatorname{arcsec} x \, dx = \int y \sec y \tan y \, dy$$

This requires integration by parts:

Let $u = y$, $dv = \sec y \tan y \, dy$,  $du = dy$,  $v = \sec y$

$$= y\sec y - \int \sec y, dy$$

$$= y\sec y - \ln|\sec y + \tan y| + C$$

Back-substitute: $y = \operatorname{arcsec} x$, $\sec y = x$

For $\tan y$: $\tan^2 y = \sec^2 y - 1 = x^2 - 1$, so $\tan y = \sqrt{x^2-1}$ (positive for $y \in [0,\pi/2)$)

$$= x\operatorname{arcsec} x - \ln|x + \sqrt{x^2-1}| + C$$

**Answer:** $\boxed{x\operatorname{arcsec} x - \ln|x+\sqrt{x^2-1}| + C}$

------

**Inverse Hyperbolic Functions**

**Example 2.2.5:** $\int \operatorname{arsinh} x \, dx$

Let $y = \operatorname{arsinh} x$, so $x = \sinh y$ and $dx = \cosh y \, dy$

$$\int \operatorname{arsinh} x \, dx = \int y \cosh y \, dy$$

Integration by parts: $u = y$, $dv = \cosh y \, dy$,  $du = dy$,  $v = \sinh y$

$$= y\sinh y - \int \sinh y, dy = y\sinh y - \cosh y + C$$

Back-substitute: $y = \operatorname{arsinh} x$, $\sinh y = x$

For $\cosh y$: $\cosh^2 y = 1 + \sinh^2 y = 1 + x^2$, so $\cosh y = \sqrt{1+x^2}$

**Answer:** $\boxed{x\operatorname{arsinh} x - \sqrt{x^2+1} + C}$

**Alternative form:** Since $\operatorname{arsinh} x = \ln(x + \sqrt{x^2+1})$:

$$= x\ln(x+\sqrt{x^2+1}) - \sqrt{x^2+1} + C$$

------

**Example 2.2.6:** $\int \operatorname{arcosh} x \, dx$ (for $x \geq 1$)

Let $y = \operatorname{arcosh} x$, so $x = \cosh y$ and $dx = \sinh y \, dy$

$$\int \operatorname{arcosh} x \, dx = \int y \sinh y \, dy$$

Integration by parts: $u = y$, $dv = \sinh y \, dy$,  $du = dy$,  $v = \cosh y$

$$= y\cosh y - \int \cosh y, dy = y\cosh y - \sinh y + C$$

Back-substitute: $y = \operatorname{arcosh} x$, $\cosh y = x$

For $\sinh y$: $\sinh^2 y = \cosh^2 y - 1 = x^2 - 1$, so $\sinh y = \sqrt{x^2-1}$ (positive for $y > 0$)

**Answer:** $\boxed{x\operatorname{arcosh} x - \sqrt{x^2-1} + C}$

------

**Example 2.2.7:** $\int \operatorname{artanh} x \, dx$ (for $|x| < 1$)

Let $y = \operatorname{artanh} x$, so $x = \tanh y$ and $dx = \operatorname{sech}^2 y \, dy$

$$\int \operatorname{artanh} x \, dx = \int y \operatorname{sech}^2 y \, dy$$

Integration by parts: $u = y$, $dv = \operatorname{sech}^2 y \, dy$,  $du = dy$,  $v = \tanh y$

$$= y\tanh y - \int \tanh y, dy$$

Recall: $\int \tanh y\, dy = \ln(\cosh y) + C$

$$= y\tanh y - \ln(\cosh y) + C$$

Back-substitute: $y = \operatorname{artanh} x$, $\tanh y = x$

For $\cosh y$: $\operatorname{sech}^2 y = 1 - \tanh^2 y = 1 - x^2$, so $\cosh y = \frac{1}{\sqrt{1-x^2}}$

$$= x\operatorname{artanh} x - \ln\left(\frac{1}{\sqrt{1-x^2}}\right) + C$$

$$= x\operatorname{artanh} x + \frac{1}{2}\ln(1-x^2) + C$$

**Answer:** $\boxed{x\operatorname{artanh} x + \frac{1}{2}\ln(1-x^2) + C}$

------

**Example 2.2.8:** $\int \operatorname{arcoth} x \, dx$ (for $|x| > 1$)

Let $y = \operatorname{arcoth} x$, so $x = \coth y$ and $dx = -\operatorname{csch}^2 y \, dy$

$$\int \operatorname{arcoth} x \, dx = \int y \cdot (-\operatorname{csch}^2 y)dy = -\int y\operatorname{csch}^2 y \, dy$$

Integration by parts: $u = y$, $dv = \operatorname{csch}^2 y \, dy$,  $du = dy$,  $v = -\coth y$

$$= -(-y\coth y + \int \coth y, dy) = y\coth y - \ln|\sinh y| + C$$

Back-substitute: $y = \operatorname{arcoth} x$, $\coth y = x$

For $\sinh y$: $\operatorname{csch}^2 y = \coth^2 y - 1 = x^2 - 1$, so $|\sinh y| = \frac{1}{\sqrt{x^2-1}}$

$$= x\operatorname{arcoth} x - \ln\left(\frac{1}{\sqrt{x^2-1}}\right) + C$$

$$= x\operatorname{arcoth} x + \frac{1}{2}\ln(x^2-1) + C$$

**Answer:** $\boxed{x\operatorname{arcoth} x + \frac{1}{2}\ln(x^2-1) + C}$

------

### 2.3 Logarithmic Powers

**Reduction Formula for $\int (\ln x)^n dx$**

**Derivation:**

Use integration by parts with $u = (\ln x)^n$ and $dv = dx$:

- $du = n(\ln x)^{n-1} \cdot \frac{1}{x}dx$
- $v = x$

$$I_n = \int (\ln x)^n dx = x(\ln x)^n - \int x \cdot n(\ln x)^{n-1} \cdot \frac{1}{x}dx$$

$$= x(\ln x)^n - n\int (\ln x)^{n-1}dx$$

$$= x(\ln x)^n - nI_{n-1}$$

**The Reduction Formula:** $$\boxed{I_n = x(\ln x)^n - nI_{n-1}}$$

**Base Case:** $I_0 = \int 1 \, dx = x + C$

------

**Example 2.3.1:** Evaluate $\int (\ln x)^3 dx$

**Solution:**

Using the reduction formula repeatedly:

$$I_3 = x(\ln x)^3 - 3I_2$$

$$I_2 = x(\ln x)^2 - 2I_1$$

$$I_1 = x\ln x - I_0 = x\ln x - x$$

Back-substitute:

$$I_2 = x(\ln x)^2 - 2(x\ln x - x) = x(\ln x)^2 - 2x\ln x + 2x$$

$$I_3 = x(\ln x)^3 - 3[x(\ln x)^2 - 2x\ln x + 2x]$$

$$= x(\ln x)^3 - 3x(\ln x)^2 + 6x\ln x - 6x + C$$

**Answer:** $\boxed{x(\ln x)^3 - 3x(\ln x)^2 + 6x\ln x - 6x + C}$

Notice that the coefficients are related to $3!$ times alternating signs. In general:

$$I_n = x\sum_{k=0}^n (-1)^{n-k}\frac{n!}{k!}(\ln x)^k + C$$

------

**Example 2.3.2:** Evaluate $\int x^2(\ln x)^2 dx$

**Solution:**

This combines polynomial and logarithmic factors. Use integration by parts with $u = (\ln x)^2$, $dv = x^2 dx$:

- $du = 2(\ln x) \cdot \frac{1}{x}dx$
- $v = \frac{x^3}{3}$

$$\int x^2(\ln x)^2 dx = \frac{x^3}{3}(\ln x)^2 - \int \frac{x^3}{3} \cdot \frac{2\ln x}{x}dx$$

$$= \frac{x^3(\ln x)^2}{3} - \frac{2}{3}\int x^2 \ln x \, dx$$

Now integrate $\int x^2\ln x \, dx$ using IBP again:

Let $u = \ln x$, $dv = x^2 dx$:

- $du = \frac{1}{x}dx$
- $v = \frac{x^3}{3}$

$$\int x^2\ln x \, dx = \frac{x^3\ln x}{3} - \int \frac{x^3}{3} \cdot \frac{1}{x}dx = \frac{x^3\ln x}{3} - \frac{1}{3}\int x^2 dx$$

$$= \frac{x^3\ln x}{3} - \frac{x^3}{9}$$

Substitute back:

$$\int x^2(\ln x)^2 dx = \frac{x^3(\ln x)^2}{3} - \frac{2}{3}\left(\frac{x^3\ln x}{3} - \frac{x^3}{9}\right) + C$$

$$= \frac{x^3(\ln x)^2}{3} - \frac{2x^3\ln x}{9} + \frac{2x^3}{27} + C$$



---

## Part II: Trigonometric and Hyperbolic Integrals

头痒痒的很正常，要开始长脑子了。

### 3. Trigonometric Power Reduction

Integrals of the form $\int \sin^m(x)\cos^n(x)dx$ are ubiquitous in applications ranging from Fourier analysis to quantum mechanics. The strategy depends critically on the parity of $m$ and $n$.

------

### 3.1 Sine and Cosine Powers

The key insight is that $\sin^2(x) + \cos^2(x) = 1$ allows us to convert between sine and cosine.

**Case 1: At least one exponent is odd**

- Save one factor of the odd power for the differential
- Convert the remaining even power using $\sin^2 + \cos^2 = 1$
- Substitute

**Case 2: Both exponents are even**

- Use half-angle formulas:
  - $\sin^2(x) = \frac{1-\cos(2x)}{2}$
  - $\cos^2(x) = \frac{1+\cos(2x)}{2}$
- Or use complex exponentials (Euler's formula)

------

**Method 1 - Traditional Substitution**

**Example 3.1.1:** Evaluate $\int \cos^3(x) \ \, dx$

**Solution:**

The exponent 3 is odd, so save one cosine factor for $du$.

$$\int \cos^3(x) \ \, dx = \int \cos^2(x) \cdot \cos(x) \ \, dx$$

Use $\cos^2(x) = 1 - \sin^2(x)$:

$$= \int (1-\sin^2(x))\cos(x) \ \, dx$$

Let $u = \sin(x)$, then $du = \cos(x)dx$:

$$= \int (1-u^2)du = u - \frac{u^3}{3} + C$$

$$= \sin(x) - \frac{\sin^3(x)}{3} + C$$

------

**Method 2 - Complex Exponentials (Euler's Formula)**

This method is more systematic for higher powers and reveals beautiful patterns.

**Recall:** $e^{ix} = \cos(x) + i\sin(x)$, therefore: $$\cos(x) = \frac{e^{ix} + e^{-ix}}{2}, \quad \sin(x) = \frac{e^{ix} - e^{-ix}}{2i}$$

**Example 3.1.2:** Evaluate $\int \cos^3(x) \ \, dx$ (using complex method)

**Solution:**

$$\cos^3(x) = \left(\frac{e^{ix} + e^{-ix}}{2}\right)^3 = \frac{1}{8}(e^{ix} + e^{-ix})^3$$

Expand using the binomial theorem: $$(e^{ix} + e^{-ix})^3 = e^{3ix} + 3e^{ix} + 3e^{-ix} + e^{-3ix}$$

Group terms: $$= (e^{3ix} + e^{-3ix}) + 3(e^{ix} + e^{-ix})$$

$$= 2\cos(3x) + 6\cos(x)$$

Therefore: $$\cos^3(x) = \frac{1}{8}[2\cos(3x) + 6\cos(x)] = \frac{\cos(3x)}{4} + \frac{3\cos(x)}{4}$$

Integrate: $$\int \cos^3(x) \ \, dx = \int \left[\frac{\cos(3x)}{4} + \frac{3\cos(x)}{4}\right]dx$$

$$= \frac{\sin(3x)}{12} + \frac{3\sin(x)}{4} + C$$

**Verification that both answers are equivalent:**

Using the triple-angle formula: $\sin(3x) = 3\sin(x) - 4\sin^3(x)$

$$\frac{\sin(3x)}{12} + \frac{3\sin(x)}{4} = \frac{3\sin(x) - 4\sin^3(x)}{12} + \frac{3\sin(x)}{4}$$

$$= \frac{3\sin(x) - 4\sin^3(x) + 9\sin(x)}{12} = \frac{12\sin(x) - 4\sin^3(x)}{12}$$

$$= \sin(x) - \frac{\sin^3(x)}{3}$$ ✓

------

**General Reduction Formulas**

For systematic computation of higher powers, we can derive reduction formulas using integration by parts.

**For $\int \cos^n(x)dx$:**

Write $\int \cos^n(x)dx = \int \cos^{n-1}(x) \cdot \cos(x)dx$

IBP: $u = \cos^{n-1}(x)$,  $dv = \cos(x)dx$

- $du = (n-1)\cos^{n-2}(x) \cdot (-\sin(x))dx$
- $v = \sin(x)$

$$\int \cos^n(x)dx = \cos^{n-1}(x)\sin(x) + (n-1)\int \cos^{n-2}(x)\sin^2(x)dx$$

Use $\sin^2(x) = 1 - \cos^2(x)$:

$$= \cos^{n-1}(x)\sin(x) + (n-1)\int \cos^{n-2}(x)[1-\cos^2(x)]dx$$

$$= \cos^{n-1}(x)\sin(x) + (n-1)\int \cos^{n-2}(x)dx - (n-1)\int \cos^n(x)dx$$

Let $I_n = \int \cos^n(x)dx$:

$$I_n = \cos^{n-1}(x)\sin(x) + (n-1)I_{n-2} - (n-1)I_n$$

$$I_n + (n-1)I_n = \cos^{n-1}(x)\sin(x) + (n-1)I_{n-2}$$

$$nI_n = \cos^{n-1}(x)\sin(x) + (n-1)I_{n-2}$$

$$\boxed{\int \cos^n(x)dx = \frac{\cos^{n-1}(x)\sin(x)}{n} + \frac{n-1}{n}\int \cos^{n-2}(x)dx}$$

$$\boxed{\int \sin^n(x)dx = -\frac{\sin^{n-1}(x)\cos(x)}{n} + \frac{n-1}{n}\int \sin^{n-2}(x)dx}$$

------

**Example 3.1.3:** Evaluate $\int \sin^4(x) \ \, dx$

**Solution:**

**Method 1 (Half-angle formulas):**

$$\sin^2(x) = \frac{1-\cos(2x)}{2}$$

$$\sin^4(x) = \left(\frac{1-\cos(2x)}{2}\right)^2 = \frac{1 - 2\cos(2x) + \cos^2(2x)}{4}$$

For $\cos^2(2x)$, use the half-angle formula again: $$\cos^2(2x) = \frac{1+\cos(4x)}{2}$$

Therefore: $$\sin^4(x) = \frac{1 - 2\cos(2x) + \frac{1+\cos(4x)}{2}}{4}$$

$$= \frac{2 - 4\cos(2x) + 1 + \cos(4x)}{8} = \frac{3 - 4\cos(2x) + \cos(4x)}{8}$$

Integrate: $$\int \sin^4(x)dx = \int \frac{3 - 4\cos(2x) + \cos(4x)}{8}dx$$

$$= \frac{1}{8}\left[3x - 2\sin(2x) + \frac{\sin(4x)}{4}\right] + C$$

$$= \frac{3x}{8} - \frac{\sin(2x)}{4} + \frac{\sin(4x)}{32} + C$$

------

**Example 3.1.4:** Evaluate $\int \cos^6(x) \ \, dx$

**Solution:**

**Method 1 (Repeated reduction formula):**

$$I_6 = \frac{\cos^5(x)\sin(x)}{6} + \frac{5}{6}I_4$$

$$I_4 = \frac{\cos^3(x)\sin(x)}{4} + \frac{3}{4}I_2$$

$$I_2 = \frac{\cos(x)\sin(x)}{2} + \frac{1}{2}I_0$$

$$I_0 = \int dx = x$$

Back-substitute: $$I_2 = \frac{\cos(x)\sin(x)}{2} + \frac{x}{2}$$

$$I_4 = \frac{\cos^3(x)\sin(x)}{4} + \frac{3}{4}\left[\frac{\cos(x)\sin(x)}{2} + \frac{x}{2}\right]$$

$$= \frac{\cos^3(x)\sin(x)}{4} + \frac{3\cos(x)\sin(x)}{8} + \frac{3x}{8}$$

$$I_6 = \frac{\cos^5(x)\sin(x)}{6} + \frac{5}{6}\left[\frac{\cos^3(x)\sin(x)}{4} + \frac{3\cos(x)\sin(x)}{8} + \frac{3x}{8}\right]$$

$$= \frac{\cos^5(x)\sin(x)}{6} + \frac{5\cos^3(x)\sin(x)}{24} + \frac{5\cos(x)\sin(x)}{16} + \frac{5x}{16}$$

**Method 2 (Complex exponentials):**

$$\cos^6(x) = \left(\frac{e^{ix}+e^{-ix}}{2}\right)^6 = \frac{1}{64}(e^{ix}+e^{-ix})^6$$

Using the binomial theorem: $$(e^{ix}+e^{-ix})^6 = \sum_{k=0}^6 \binom{6}{k}e^{i(6-2k)x}$$

$$= e^{6ix} + 6e^{4ix} + 15e^{2ix} + 20 + 15e^{-2ix} + 6e^{-4ix} + e^{-6ix}$$

Group conjugate pairs: $$= (e^{6ix}+e^{-6ix}) + 6(e^{4ix}+e^{-4ix}) + 15(e^{2ix}+e^{-2ix}) + 20$$

$$= 2\cos(6x) + 12\cos(4x) + 30\cos(2x) + 20$$

Therefore: $$\cos^6(x) = \frac{1}{64}[2\cos(6x) + 12\cos(4x) + 30\cos(2x) + 20]$$

$$= \frac{\cos(6x)}{32} + \frac{3\cos(4x)}{16} + \frac{15\cos(2x)}{32} + \frac{5}{16}$$

Integrate: $$\int \cos^6(x)dx = \frac{\sin(6x)}{192} + \frac{3\sin(4x)}{64} + \frac{15\sin(2x)}{64} + \frac{5x}{16} + C$$

------

**Example 3.1.5:** Evaluate $\int \sin^5(x) \ \, dx$

**Solution:**

The exponent is odd, so use the substitution method.

$$\int \sin^5(x)dx = \int \sin^4(x) \cdot \sin(x)dx$$

$$= \int (\sin^2(x))^2 \sin(x)dx = \int (1-\cos^2(x))^2 \sin(x)dx$$

Let $u = \cos(x)$, then $du = -\sin(x)dx$:

$$= -\int (1-u^2)^2 du = -\int (1 - 2u^2 + u^4)du$$

$$= -\left(u - \frac{2u^3}{3} + \frac{u^5}{5}\right) + C$$

$$= -\cos(x) + \frac{2\cos^3(x)}{3} - \frac{\cos^5(x)}{5} + C$$

------

**Example 3.1.6:** Evaluate $\int \cos^7(x) \ \, dx$

**Solution:**

$$\int \cos^7(x)dx = \int \cos^6(x)\cos(x)dx = \int (\cos^2(x))^3 \cos(x)dx$$

$$= \int (1-\sin^2(x))^3 \cos(x)dx$$

Let $u = \sin(x)$, then $du = \cos(x)dx$:

$$= \int (1-u^2)^3 du$$

Expand $(1-u^2)^3$: $$(1-u^2)^3 = 1 - 3u^2 + 3u^4 - u^6$$

$$= \int (1 - 3u^2 + 3u^4 - u^6)du$$

$$= u - u^3 + \frac{3u^5}{5} - \frac{u^7}{7} + C$$

$$= \sin(x) - \sin^3(x) + \frac{3\sin^5(x)}{5} - \frac{\sin^7(x)}{7} + C$$

------

### 3.2 Mixed Sine-Cosine Powers

For integrals of the form $\int \sin^m(x)\cos^n(x)dx$, the strategy depends on the parity of $m$ and $n$.

**Strategy Decision Tree:**

1. **If $m$ is odd:** Save one $\sin(x)$ for $du$, convert remaining $\sin^{m-1}(x)$ using $\sin^2 = 1-\cos^2$, substitute $u = \cos(x)$
2. **If $n$ is odd:** Save one $\cos(x)$ for $du$, convert remaining $\cos^{n-1}(x)$ using $\cos^2 = 1-\sin^2$, substitute $u = \sin(x)$
3. **If both $m$ and $n$ are odd:** Choose either strategy (typically the one with smaller exponent)
4. **If both $m$ and $n$ are even:** Use half-angle formulas repeatedly or product-to-sum identities

------

**Example 3.2.1:** Evaluate $\int \sin^3(x)\cos^2(x) \ \, dx$

**Solution:**

Since the sine exponent (3) is odd, save one $\sin(x)$ and convert the rest.

$$\int \sin^3(x)\cos^2(x)dx = \int \sin^2(x)\cos^2(x)\sin(x)dx$$

$$= \int (1-\cos^2(x))\cos^2(x)\sin(x)dx$$

Let $u = \cos(x)$, then $du = -\sin(x)dx$:

$$= -\int (1-u^2)u^2 du = -\int (u^2 - u^4)du$$

$$= -\left(\frac{u^3}{3} - \frac{u^5}{5}\right) + C$$

$$= -\frac{\cos^3(x)}{3} + \frac{\cos^5(x)}{5} + C$$

------

**Example 3.2.2:** Evaluate $\int \sin^2(x)\cos^4(x) \ \, dx$

**Solution:**

Both exponents are even, so use half-angle formulas.

$$\sin^2(x) = \frac{1-\cos(2x)}{2}, \quad \cos^2(x) = \frac{1+\cos(2x)}{2}$$

$$\int \sin^2(x)\cos^4(x)dx = \int \frac{1-\cos(2x)}{2} \cdot \left(\frac{1+\cos(2x)}{2}\right)^2 dx$$

$$= \frac{1}{8}\int (1-\cos(2x))(1+\cos(2x))^2 dx$$

$$= \frac{1}{8}\int [1 + \cos(2x) - \cos^2(2x) - \cos^3(2x)]dx$$

For $\cos^2(2x)$, use $\cos^2(2x) = \frac{1+\cos(4x)}{2}$:

$$= \frac{1}{8}\int \left[\frac{1}{2} + \cos(2x) - \frac{\cos(4x)}{2} - \cos^3(2x)\right]dx$$

For $\cos^3(2x)$, use $\cos^3(2x) = \frac{\cos(6x)}{4} + \frac{3\cos(2x)}{4}$ (from earlier):

$$= \frac{1}{8}\int \left[\frac{1}{2} + \cos(2x) - \frac{\cos(4x)}{2} - \frac{\cos(6x)}{4} - \frac{3\cos(2x)}{4}\right]dx$$

$$= \frac{x}{16} + \frac{\sin(2x)}{64} - \frac{\sin(4x)}{64} - \frac{\sin(6x)}{192} + C$$

------

**Example 3.2.3:** Evaluate $\int \sin^3(x)\cos^3(x) \ \, dx$

**Solution:**

Both exponents are odd. We can choose either; let's use $u = \sin(x)$ (saving one $\cos(x)$).

$$\int \sin^3(x)\cos^3(x)dx = \int \sin^3(x)\cos^2(x)\cos(x)dx$$

$$= \int \sin^3(x)(1-\sin^2(x))\cos(x)dx$$

Let $u = \sin(x)$, $du = \cos(x)dx$:

$$= \int u^3(1-u^2)du = \int (u^3 - u^5)du$$

$$= \frac{u^4}{4} - \frac{u^6}{6} + C$$

$$= \frac{\sin^4(x)}{4} - \frac{\sin^6(x)}{6} + C$$

**Alternative approach (using $u = \cos(x)$):**

$$\int \sin^3(x)\cos^3(x)dx = \int \sin^2(x)\cos^3(x)\sin(x)dx$$

$$= \int (1-\cos^2(x))\cos^3(x)\sin(x)dx$$

Let $u = \cos(x)$, $du = -\sin(x)dx$:

$$= -\int (1-u^2)u^3 du = -\int (u^3 - u^5)du$$

$$= -\left(\frac{u^4}{4} - \frac{u^6}{6}\right) + C = -\frac{\cos^4(x)}{4} + \frac{\cos^6(x)}{6} + C$$

Both answers are correct and differ by a constant (which can be verified using the identity $\sin^2 + \cos^2 = 1$).

------

### 3.3 Hyperbolic Power Formulas

Hyperbolic functions follow similar patterns to trigonometric functions but with key sign differences in their identities.

**Key Identities:** $$\cosh^2(x) - \sinh^2(x) = 1$$ $$\sinh(2x) = 2\sinh(x)\cosh(x)$$ $$\cosh(2x) = \cosh^2(x) + \sinh^2(x) = 2\cosh^2(x) - 1 = 1 + 2\sinh^2(x)$$

**Half-argument formulas:** $$\sinh^2(x) = \frac{\cosh(2x) - 1}{2}$$ $$\cosh^2(x) = \frac{\cosh(2x) + 1}{2}$$

------

**General Reduction Formulas:**

**For $\int \sinh^n(x)dx$:**

Write $\int \sinh^n(x)dx = \int \sinh^{n-1}(x)\sinh(x)dx$

IBP: $u = \sinh^{n-1}(x)$, $dv = \sinh(x)dx$

- $du = (n-1)\sinh^{n-2}(x)\cosh(x)dx$
- $v = \cosh(x)$

$$\int \sinh^n(x)dx = \sinh^{n-1}(x)\cosh(x) - (n-1)\int \sinh^{n-2}(x)\cosh^2(x)dx$$

Use $\cosh^2(x) = 1 + \sinh^2(x)$:

$$= \sinh^{n-1}(x)\cosh(x) - (n-1)\int \sinh^{n-2}(x)[1+\sinh^2(x)]dx$$

$$= \sinh^{n-1}(x)\cosh(x) - (n-1)\int \sinh^{n-2}(x)dx - (n-1)\int \sinh^n(x)dx$$

Let $I_n = \int \sinh^n(x)dx$:

$$I_n = \sinh^{n-1}(x)\cosh(x) - (n-1)I_{n-2} - (n-1)I_n$$

$$I_n + (n-1)I_n = \sinh^{n-1}(x)\cosh(x) - (n-1)I_{n-2}$$

$$nI_n = \sinh^{n-1}(x)\cosh(x) - (n-1)I_{n-2}$$

$$\boxed{\int \sinh^n(x)dx = \frac{\sinh^{n-1}(x)\cosh(x)}{n} - \frac{n-1}{n}\int \sinh^{n-2}(x)dx}$$

**For $\int \cosh^n(x)dx$:**

Similarly, using $\sinh^2(x) = \cosh^2(x) - 1$:

$$\boxed{\int \cosh^n(x)dx = \frac{\cosh^{n-1}(x)\sinh(x)}{n} + \frac{n-1}{n}\int \cosh^{n-2}(x)dx}$$

Note the sign difference compared to trig functions!

------

**Example 3.3.1:** Evaluate $\int \sinh^4(x) \ \, dx$

**Solution:**

**Method 1 (Reduction formula):**

$$I_4 = \frac{\sinh^3(x)\cosh(x)}{4} - \frac{3}{4}I_2$$

$$I_2 = \frac{\sinh(x)\cosh(x)}{2} - \frac{1}{2}I_0$$

$$I_0 = \int dx = x$$

Back-substitute: $$I_2 = \frac{\sinh(x)\cosh(x)}{2} - \frac{x}{2}$$

$$I_4 = \frac{\sinh^3(x)\cosh(x)}{4} - \frac{3}{4}\left[\frac{\sinh(x)\cosh(x)}{2} - \frac{x}{2}\right]$$

$$= \frac{\sinh^3(x)\cosh(x)}{4} - \frac{3\sinh(x)\cosh(x)}{8} + \frac{3x}{8}$$

**Method 2 (Exponential):**

$$\sinh(x) = \frac{e^x - e^{-x}}{2}$$

$$\sinh^4(x) = \frac{(e^x - e^{-x})^4}{16}$$

Expand using the binomial theorem: $$(e^x - e^{-x})^4 = e^{4x} - 4e^{2x} + 6 - 4e^{-2x} + e^{-4x}$$

Group terms: $$= (e^{4x} + e^{-4x}) - 4(e^{2x} + e^{-2x}) + 6$$

$$= 2\cosh(4x) - 8\cosh(2x) + 6$$

Therefore: $$\sinh^4(x) = \frac{2\cosh(4x) - 8\cosh(2x) + 6}{16} = \frac{\cosh(4x)}{8} - \frac{\cosh(2x)}{2} + \frac{3}{8}$$

Integrate: $$\int \sinh^4(x)dx = \frac{\sinh(4x)}{32} - \frac{\sinh(2x)}{4} + \frac{3x}{8} + C$$

------

**Example 3.3.2:** Evaluate $\int \cosh^3(x) \ \, dx$

**Solution:**

**Method 1 (Direct substitution):**

$$\int \cosh^3(x)dx = \int \cosh^2(x)\cosh(x)dx$$

Use $\cosh^2(x) = 1 + \sinh^2(x)$:

$$= \int (1 + \sinh^2(x))\cosh(x)dx$$

Let $u = \sinh(x)$, $du = \cosh(x)dx$:

$$= \int (1 + u^2)du = u + \frac{u^3}{3} + C$$

$$= \sinh(x) + \frac{\sinh^3(x)}{3} + C$$

**Method 2 (Exponential):**

$$\cosh^3(x) = \left(\frac{e^x + e^{-x}}{2}\right)^3 = \frac{(e^x + e^{-x})^3}{8}$$

$$= \frac{e^{3x} + 3e^x + 3e^{-x} + e^{-3x}}{8}$$

$$= \frac{(e^{3x} + e^{-3x}) + 3(e^x + e^{-x})}{8} = \frac{2\cosh(3x) + 6\cosh(x)}{8}$$

$$= \frac{\cosh(3x)}{4} + \frac{3\cosh(x)}{4}$$

Integrate: $$\int \cosh^3(x)dx = \frac{\sinh(3x)}{12} + \frac{3\sinh(x)}{4} + C$$

Using the triple-angle formula $\sinh(3x) = 3\sinh(x) + 4\sinh^3(x)$:

$$\frac{\sinh(3x)}{12} + \frac{3\sinh(x)}{4} = \frac{3\sinh(x) + 4\sinh^3(x)}{12} + \frac{3\sinh(x)}{4}$$

$$= \frac{3\sinh(x) + 4\sinh^3(x) + 9\sinh(x)}{12} = \sinh(x) + \frac{\sinh^3(x)}{3}$$ ✓

------

**Example 3.3.3:** Evaluate $\int \sinh^5(x) \ \, dx$

**Solution:**

$$\int \sinh^5(x)dx = \int \sinh^4(x)\sinh(x)dx$$

$$= \int (\sinh^2(x))^2 \sinh(x)dx$$

Use $\sinh^2(x) = \cosh^2(x) - 1$:

$$= \int (\cosh^2(x) - 1)^2 \sinh(x)dx$$

Let $u = \cosh(x)$, $du = \sinh(x)dx$:

$$= \int (u^2 - 1)^2 du = \int (u^4 - 2u^2 + 1)du$$

$$= \frac{u^5}{5} - \frac{2u^3}{3} + u + C$$

$$= \frac{\cosh^5(x)}{5} - \frac{2\cosh^3(x)}{3} + \cosh(x) + C$$

------

**Example 3.3.4:** Evaluate $\int \cosh^4(x) \ \, dx$

**Solution:**

Using the exponential method:

$$\cosh^4(x) = \left(\frac{e^x + e^{-x}}{2}\right)^4 = \frac{(e^x + e^{-x})^4}{16}$$

$$(e^x + e^{-x})^4 = e^{4x} + 4e^{2x} + 6 + 4e^{-2x} + e^{-4x}$$

$$= (e^{4x} + e^{-4x}) + 4(e^{2x} + e^{-2x}) + 6$$

$$= 2\cosh(4x) + 8\cosh(2x) + 6$$

Therefore: $$\cosh^4(x) = \frac{\cosh(4x)}{8} + \frac{\cosh(2x)}{2} + \frac{3}{8}$$

Integrate: $$\int \cosh^4(x)dx = \frac{\sinh(4x)}{32} + \frac{\sinh(2x)}{4} + \frac{3x}{8} + C$$

------

**Example 3.3.5:** Evaluate $\int \sinh^2(x)\cosh^2(x) \ \, dx$

**Solution:**

Use the identity $\sinh(x)\cosh(x) = \frac{\sinh(2x)}{2}$:

$$\sinh^2(x)\cosh^2(x) = [\sinh(x)\cosh(x)]^2 = \left[\frac{\sinh(2x)}{2}\right]^2 = \frac{\sinh^2(2x)}{4}$$

Use $\sinh^2(2x) = \frac{\cosh(4x) - 1}{2}$:

$$= \frac{1}{4} \cdot \frac{\cosh(4x) - 1}{2} = \frac{\cosh(4x) - 1}{8}$$

Integrate: $$\int \sinh^2(x)\cosh^2(x)dx = \int \frac{\cosh(4x) - 1}{8}dx$$

$$= \frac{1}{8}\left[\frac{\sinh(4x)}{4} - x\right] + C$$

$$= \frac{\sinh(4x)}{32} - \frac{x}{8} + C$$

------

### 3.4 Hyperbolic Secant and Cosecant

These integrals require special techniques and often result in unexpected forms.

**Example 3.4.1:** Evaluate $\int \operatorname{sech}(x) \ \, dx$

**Solution:**

**Method 1 (Multiply by conjugate):**

Multiply numerator and denominator by $\operatorname{sech}(x) + \tanh(x)$:

$$\int \operatorname{sech}(x)dx = \int \frac{\operatorname{sech}(x)[\operatorname{sech}(x) - \tanh(x)]}{\operatorname{sech}(x) + \tanh(x)}dx = \ln|\operatorname{sech}(x) - \tanh(x)| + C$$

**Method 2 (Convert to exponentials):**

$$\operatorname{sech}(x) = \frac{1}{\cosh(x)} = \frac{2}{e^x + e^{-x}}$$

Multiply numerator and denominator by $e^x$:

$$= \frac{2e^x}{e^{2x} + 1}$$

Let $u = e^x$, $du = e^x dx$, so $dx = \frac{du}{u}$:

$$\int \frac{2e^x}{e^{2x}+1}dx = \int \frac{2}{u^2+1}du = 2\arctan(u) + C$$

$$= 2\arctan(e^x) + C$$

**Method 3 (Using substitution):**

$$\int \operatorname{sech}(x)dx = \int \frac{\cosh(x)}{\cosh^2(x)}dx$$

Let $u = \sinh(x)$, then $du = \cosh(x)dx$:

$$= \int \frac{1}{1 + u^2} du = \arctan(u) + C = \arctan(\sinh(x)) + C$$

Detailed proof of equivalence requires the complex definition of arctan, which will not be covered here.

**Answer:** $\boxed{2\arctan(e^x) + C}$, or $\boxed{\ln|\operatorname{sech}(x) - \tanh(x)| + C}$, or $\boxed{\arctan(\sinh(x)) + C}$

------

**Example 3.4.2:** Evaluate $\int \operatorname{sech}^2(x)\tanh(x) \, dx$

**Solution:**

Notice that $\frac{d}{dx}[\operatorname{sech}(x)] = -\operatorname{sech}(x)\tanh(x)$.

So $\operatorname{sech}(x)\tanh(x)$ is almost the derivative of $\operatorname{sech}(x)$.

$$\int \operatorname{sech}^2(x)\tanh(x)dx = \int \operatorname{sech}(x) \cdot [\operatorname{sech}(x)\tanh(x)]dx$$

Let $u = \operatorname{sech}(x)$, then $du = -\operatorname{sech}(x)\tanh(x)dx$:

$$= -\int u , du = -\frac{u^2}{2} + C$$

$$= -\frac{\operatorname{sech}^2(x)}{2} + C$$

**Answer:** $\boxed{-\frac{\operatorname{sech}^2(x)}{2} + C}$

------

**Example 3.4.3:** Evaluate $\int \operatorname{csch}^3(x) \, dx$

**Solution:**

This requires integration by parts combined with reduction.

Write $\int \operatorname{csch}^3(x)dx = \int \operatorname{csch}^2(x) \cdot \operatorname{csch}(x)dx$

IBP: $u = \operatorname{csch}(x)$, $dv = \operatorname{csch}^2(x)dx$

- $du = -\operatorname{csch}(x)\coth(x)dx$
- $v = -\coth(x)$

$$\int \operatorname{csch}^3(x)dx = -\operatorname{csch}(x)\coth(x) - \int \coth(x) \cdot \operatorname{csch}(x)\coth(x)dx$$

$$= -\operatorname{csch}(x)\coth(x) - \int \operatorname{csch}(x)\coth^2(x)dx$$

Use $\coth^2(x) = 1 + \operatorname{csch}^2(x)$:

$$= -\operatorname{csch}(x)\coth(x) - \int \operatorname{csch}(x)[1 + \operatorname{csch}^2(x)]dx$$

$$= -\operatorname{csch}(x)\coth(x) - \int \operatorname{csch}(x)dx - \int \operatorname{csch}^3(x)dx$$

Let $I = \int \operatorname{csch}^3(x)dx$:

$$I = -\operatorname{csch}(x)\coth(x) - \ln|\tanh(x/2)| - I$$

$$2I = -\operatorname{csch}(x)\coth(x) - \ln|\tanh(x/2)|$$

$$I = -\frac{\operatorname{csch}(x)\coth(x)}{2} - \frac{\ln|\tanh(x/2)|}{2} + C$$

**Answer:** $\boxed{-\frac{\operatorname{csch}(x)\coth(x)}{2} - \frac{\ln|\tanh(x/2)|}{2} + C}$
