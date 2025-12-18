### 4. Secant-Tangent Power Reduction

Integrals involving powers of secant and tangent require careful case analysis based on parity. The fundamental relationship $\tan^2(x) = \sec^2(x) - 1$ is the key to most transformations.

---

### 4.1 Classification by Parity

To integrate $ \int \sec^m(x) \tan^n(x) \, dx $:  

- If $ m $ is odd: Save $ \sec(x)\tan(x) $, let $ u = \sec(x) $.  
- If $ m $ is even:  
  - If $ n $ is even: Extract $ \sec^2(x) $, use $ \tan^2(x) = \sec^2(x) - 1 $, let $ u = \tan(x) $.  
  - If $ n $ is odd: Use a reduction formula or special method.

**Key Differentials:**

- $d(\sec x) = \sec x \tan x  \, dx$
- $d(\tan x) = \sec^2 x  \, dx$

---

### 4.2 Secant Powers

**Secant Reduction Formula Derivation:**

For $I_n = \int \sec^n(x)dx$, write: $$I_n = \int \sec^{n-2}(x)\sec^2(x)dx$$

IBP: $u = \sec^{n-2}(x)$, $dv = \sec^2(x)dx$

- $du = (n-2)\sec^{n-3}(x) \cdot \sec(x)\tan(x)dx = (n-2)\sec^{n-2}(x)\tan(x)dx$
- $v = \tan(x)$

$$I_n = \sec^{n-2}(x)\tan(x) - (n-2)\int \sec^{n-2}(x)\tan^2(x)dx$$

Use $\tan^2(x) = \sec^2(x) - 1$:

$$= \sec^{n-2}(x)\tan(x) - (n-2)\int \sec^{n-2}(x)[\sec^2(x) - 1]dx$$

$$= \sec^{n-2}(x)\tan(x) - (n-2)\int \sec^n(x)dx + (n-2)\int \sec^{n-2}(x)dx$$

$$= \sec^{n-2}(x)\tan(x) - (n-2)I_n + (n-2)I_{n-2}$$

$$I_n + (n-2)I_n = \sec^{n-2}(x)\tan(x) + (n-2)I_{n-2}$$

$$(n-1)I_n = \sec^{n-2}(x)\tan(x) + (n-2)I_{n-2}$$

$$\boxed{\int \sec^n(x)dx = \frac{\sec^{n-2}(x)\tan(x)}{n-1} + \frac{n-2}{n-1}\int \sec^{n-2}(x)dx}$$

**Base Cases:**

$$I_0 = \int dx = x + C$$

$$I_1 = \int \sec(x)dx = \ln|\sec(x) + \tan(x)| + C$$

(Derivation of $I_1$: Multiply by $\frac{\sec x + \tan x}{\sec x + \tan x}$:

$$\int \sec(x)dx = \int \frac{\sec x(\sec x + \tan x)}{\sec x + \tan x}dx = \int \frac{\sec^2 x + \sec x \tan x}{\sec x + \tan x}dx$$

Let $u = \sec x + \tan x$, then $du = (\sec x \tan x + \sec^2 x)dx$:

$$= \int \frac{du}{u} = \ln|u| + C = \ln|\sec x + \tan x| + C$$)

---

**Example 4.2.1:** Evaluate $\int \sec^3(x) \, dx$

**Solution:**

Using the reduction formula with $n = 3$:

$$I_3 = \frac{\sec(x)\tan(x)}{2} + \frac{1}{2}I_1$$

$$I_1 = \ln|\sec(x) + \tan(x)|$$

Therefore: $$I_3 = \frac{\sec(x)\tan(x)}{2} + \frac{\ln|\sec(x) + \tan(x)|}{2} + C$$

This is a famous integral that appears frequently in applications (arc length of parabolas, catenary curves, etc.).

---

**Example 4.2.2:** Evaluate $\int \sec^5(x) \, dx$

**Solution:**

Using the reduction formula:

$$I_5 = \frac{\sec^3(x)\tan(x)}{4} + \frac{3}{4}I_3$$

We already know $I_3 = \frac{\sec(x)\tan(x)}{2} + \frac{\ln|\sec(x) + \tan(x)|}{2}$:

$$I_5 = \frac{\sec^3(x)\tan(x)}{4} + \frac{3}{4}\left[\frac{\sec(x)\tan(x)}{2} + \frac{\ln|\sec(x) + \tan(x)|}{2}\right]$$

$$= \frac{\sec^3(x)\tan(x)}{4} + \frac{3\sec(x)\tan(x)}{8} + \frac{3\ln|\sec(x) + \tan(x)|}{8} + C$$

---

**Example 4.2.3:** Evaluate $\int \sec^4(x) \, dx$

**Solution:**

The exponent is even, so we can use a different approach. Write:

$$\sec^4(x) = \sec^2(x) \cdot \sec^2(x) = (1 + \tan^2(x))\sec^2(x)$$

Let $u = \tan(x)$, $du = \sec^2(x)dx$:

$$\int \sec^4(x)dx = \int (1 + u^2)du = u + \frac{u^3}{3} + C$$

$$= \tan(x) + \frac{\tan^3(x)}{3} + C$$

---

### 4.3 Tangent Powers

**Tangent Reduction Strategy:**

For $\int \tan^n(x)dx$, use the identity $\tan^2(x) = \sec^2(x) - 1$ repeatedly.

**Tangent Reduction Formula Derivation:**

Write $\tan^n(x) = \tan^{n-2}(x) \cdot \tan^2(x) = \tan^{n-2}(x)[\sec^2(x) - 1]$:

$$\int \tan^n(x)dx = \int \tan^{n-2}(x)\sec^2(x)dx - \int \tan^{n-2}(x)dx$$

For the first integral, let $u = \tan(x)$, $du = \sec^2(x)dx$:

$$= \int u^{n-2}du - \int \tan^{n-2}(x)dx = \frac{u^{n-1}}{n-1} - \int \tan^{n-2}(x)dx$$

$$\boxed{\int \tan^n(x)dx = \frac{\tan^{n-1}(x)}{n-1} - \int \tan^{n-2}(x)dx}$$

**Base Cases:**

$$\int \tan^0(x)dx = \int dx = x + C$$

$$\int \tan(x)dx = \int \frac{\sin(x)}{\cos(x)}dx = -\ln|\cos(x)| + C = \ln|\sec(x)| + C$$

$$\int \tan^2(x)dx = \int (\sec^2(x) - 1)dx = \tan(x) - x + C$$

---

**Example 4.3.1:** Evaluate $\int \tan^4(x) \, dx$

**Solution:**

Using the reduction formula:

$$\int \tan^4(x)dx = \frac{\tan^3(x)}{3} - \int \tan^2(x)dx$$

$$= \frac{\tan^3(x)}{3} - [\tan(x) - x] + C$$

$$= \frac{\tan^3(x)}{3} - \tan(x) + x + C$$

---

**Example 4.3.2:** Evaluate $\int \tan^6(x) \, dx$

**Solution:**

$$\int \tan^6(x)dx = \frac{\tan^5(x)}{5} - \int \tan^4(x)dx$$

$$= \frac{\tan^5(x)}{5} - \left[\frac{\tan^3(x)}{3} - \tan(x) + x\right] + C$$

$$= \frac{\tan^5(x)}{5} - \frac{\tan^3(x)}{3} + \tan(x) - x + C$$

---

**Example 4.3.3:** Evaluate $\int \tan^3(x) \, dx$

**Solution:**

$$\int \tan^3(x)dx = \int \tan(x) \cdot \tan^2(x)dx = \int \tan(x)[\sec^2(x) - 1]dx$$

$$= \int \tan(x)\sec^2(x)dx - \int \tan(x)dx$$

For the first integral, let $u = \tan(x)$, $du = \sec^2(x)dx$:

$$= \int u , du - \int \tan(x)dx = \frac{u^2}{2} - \ln|\sec(x)| + C$$

$$= \frac{\tan^2(x)}{2} - \ln|\sec(x)| + C$$

$$= \frac{\tan^2(x)}{2} + \ln|\cos(x)| + C$$

---

**Example 4.3.4:** Evaluate $\int \tan^5(x) \, dx$

**Solution:**

Using the reduction formula:

$$\int \tan^5(x)dx = \frac{\tan^4(x)}{4} - \int \tan^3(x)dx$$

$$= \frac{\tan^4(x)}{4} - \frac{\tan^2(x)}{2} - \ln|\cos(x)| + C$$

---

**Example 4.3.5:** Evaluate $\int \tan^7(x) \, dx$

**Solution:**

$$\int \tan^7(x)dx = \frac{\tan^6(x)}{6} - \int \tan^5(x)dx$$

$$= \frac{\tan^6(x)}{6} - \left[\frac{\tan^4(x)}{4} - \frac{\tan^2(x)}{2} + \ln|\sec(x)|\right] + C$$

$$= \frac{\tan^6(x)}{6} - \frac{\tan^4(x)}{4} + \frac{\tan^2(x)}{2} - \ln|\sec(x)| + C$$

**Pattern Observation:**

For odd powers of tangent: $$\int \tan^{2k+1}(x)dx = \sum_{j=1}^k \frac{(-1)^{k-j}\tan^{2j}(x)}{2j} + (-1)^k\ln|\sec(x)| + C$$

For even powers: $$\int \tan^{2k}(x)dx = \sum_{j=1}^k \frac{(-1)^{k-j}\tan^{2j-1}(x)}{2j-1} + (-1)^{k+1}x + C$$

---

### 4.4 Mixed Secant-Tangent

When both secant and tangent appear with various powers, the strategy depends on identifying which differential form is present (or can be created).

**Strategy Summary:**

1. **If tangent power is odd AND secant power is at least 1:** Extract $\sec(x)\tan(x)dx = d(\sec x)$, convert remaining tangent powers using $\tan^2 = \sec^2 - 1$
2. **If tangent power is even:** Extract $\sec^2(x)dx = d(\tan x)$, convert remaining secant powers using $\sec^2 = 1 + \tan^2$
3. **Otherwise:** Use reduction formulas or convert to sines and cosines

---

**Example 4.4.1:** Evaluate $\int \tan^3(x)\sec^3(x) \, dx$

**Solution:**

Tangent power is odd, so extract $\sec(x)\tan(x)$:

$$\int \tan^3(x)\sec^3(x)dx = \int \tan^2(x)\sec^2(x) \cdot [\sec(x)\tan(x)]dx$$

Use $\tan^2(x) = \sec^2(x) - 1$:

$$= \int [\sec^4(x) - \sec^2(x)]\sec(x)\tan(x)dx$$

Let $u = \sec(x)$, $du = \sec(x)\tan(x)dx$:

$$= \int [u^4 - u^2]du = \frac{u^5}{5} - \frac{u^3}{3} + C$$

$$= \frac{\sec^5(x)}{5} - \frac{\sec^3(x)}{3} + C$$

---

**Example 4.4.2:** Evaluate $\int \tan^2(x)\sec^4(x) \, dx$

**Solution:**

Tangent power is even, so extract $\sec^2(x)$:

$$\int \tan^2(x)\sec^4(x)dx = \int \tan^2(x)\sec^2(x) \cdot \sec^2(x)dx$$

Use $\sec^2(x) = 1 + \tan^2(x)$:

$$= \int [\tan^2(x) + \tan^4(x)]\sec^2(x)dx$$

Let $u = \tan(x)$, $du = \sec^2(x)dx$:

$$= \int [u^2 + u^4]du = \frac{u^3}{3} + \frac{u^5}{5} + C$$

$$= \frac{\tan^3(x)}{3} + \frac{\tan^5(x)}{5} + C$$

---

**Example 4.4.3:** Evaluate $\int \tan^4(x)\sec(x) \, dx$

**Solution:**

Tangent power is even, but we only have $\sec(x)$ (not $\sec^2$). We need a different approach.

Convert everything to sines and cosines:

$$\int \tan^4(x)\sec(x)dx = \int \frac{\sin^4(x)}{\cos^4(x)} \cdot \frac{1}{\cos(x)}dx = \int \frac{\sin^4(x)}{\cos^5(x)}dx$$

This doesn't simplify nicely either. Let's try a substitution approach.

Write $\tan^4(x) = (\sec^2(x) - 1)^2 = \sec^4(x) - 2\sec^2(x) + 1$:

$$= \int \sec^5(x)dx - 2\int \sec^3(x)dx + \int \sec(x)dx$$

We've computed these before:

- $\int \sec^5(x)dx = \frac{\sec^3(x)\tan(x)}{4} + \frac{3\sec(x)\tan(x)}{8} + \frac{3\ln|\sec(x) + \tan(x)|}{8}$
- $\int \sec^3(x)dx = \frac{\sec(x)\tan(x)}{2} + \frac{\ln|\sec(x) + \tan(x)|}{2}$
- $\int \sec(x)dx = \ln|\sec(x) + \tan(x)|$

Therefore: $$= \frac{\sec^3(x)\tan(x)}{4} + \frac{3\sec(x)\tan(x)}{8} + \frac{3\ln|\sec(x) + \tan(x)|}{8}$$ $$\quad - 2\left[\frac{\sec(x)\tan(x)}{2} + \frac{\ln|\sec(x) + \tan(x)|}{2}\right]$$ $$\quad + \ln|\sec(x) + \tan(x)| + C$$

$$= \frac{\sec^3(x)\tan(x)}{4} - \frac{5\sec(x)\tan(x)}{8} + \frac{3\ln|\sec(x) + \tan(x)|}{8} + C$$

---

**Example 4.4.4:** Evaluate $\int \tan^5(x)\sec^3(x) \, dx$

**Solution:**

Tangent power is odd, extract $\sec(x)\tan(x)$:

$$\int \tan^5(x)\sec^3(x)dx = \int \tan^4(x)\sec^2(x) \cdot [\sec(x)\tan(x)]dx$$

Use $\tan^2(x) = \sec^2(x) - 1$, so $\tan^4(x) = (\sec^2(x) - 1)^2$:

$$= \int (\sec^2(x) - 1)^2 \sec^2(x) \cdot \sec(x)\tan(x)dx$$

$$= \int [\sec^4(x) - 2\sec^2(x) + 1]\sec^2(x) \cdot \sec(x)\tan(x)dx$$

$$= \int [\sec^6(x) - 2\sec^4(x) + \sec^2(x)]\sec(x)\tan(x)dx$$

Let $u = \sec(x)$, $du = \sec(x)\tan(x)dx$:

$$= \int [u^6 - 2u^4 + u^2]du = \frac{u^7}{7} - \frac{2u^5}{5} + \frac{u^3}{3} + C$$

$$= \frac{\sec^7(x)}{7} - \frac{2\sec^5(x)}{5} + \frac{\sec^3(x)}{3} + C$$

---

**Example 4.4.5:** Evaluate $\int \tan(x)\sec^5(x) \, dx$

**Solution:**

This is straightforward since we have $\sec(x)\tan(x)$:

Let $u = \sec(x)$, $du = \sec(x)\tan(x)dx$:

$$\int \tan(x)\sec^5(x)dx = \int \sec^4(x) \cdot [\sec(x)\tan(x)]dx$$

$$= \int u^4 du = \frac{u^5}{5} + C$$

$$= \frac{\sec^5(x)}{5} + C$$



---

## Part III: Multiplication of Polynominal, Exponential, and Trigonometric

我见分部积分多妩媚，料分部积分见我应如是。

### 5. Polynomial × Exponential

### 5.1 The Reduction Formula

For $I_n = \int x^n e^{ax}dx$, using integration by parts with $u = x^n$, $dv = e^{ax}dx$:

$$I_n = \frac{x^n e^{ax}}{a} - \frac{n}{a}I_{n-1}$$

**Base case:** $I_0 = \int e^{ax}dx = \frac{e^{ax}}{a} + C$

**Tabular Method (Efficient for multiple reductions):**

For integrals requiring multiple IBP applications, the tabular method is systematic:

| Differentiate   | Sign     | Integrate                |
| --------------- | -------- | ------------------------ |
| $x^n$           | $+$      | $\frac{e^{ax}}{a}$       |
| $nx^{n-1}$      | $-$      | $\frac{e^{ax}}{a^2}$     |
| $n(n-1)x^{n-2}$ | $+$      | $\frac{e^{ax}}{a^3}$     |
| $\vdots$        | $\vdots$ | $\vdots$                 |
| $n!$            | $(-1)^n$ | $\frac{e^{ax}}{a^{n+1}}$ |
| $0$             |          |                          |

The answer is the sum of products along the lines.

---

**Example 5.1.1:** Evaluate $\int x^3 e^{2x}dx$

**Solution (Reduction Formula):**

$$I_3 = \frac{x^3 e^{2x}}{2} - \frac{3}{2}I_2$$

$$I_2 = \frac{x^2 e^{2x}}{2} - \frac{2}{2}I_1 = \frac{x^2 e^{2x}}{2} - I_1$$

$$I_1 = \frac{x e^{2x}}{2} - \frac{1}{2}I_0 = \frac{x e^{2x}}{2} - \frac{1}{2} \cdot \frac{e^{2x}}{2} = \frac{xe^{2x}}{2} - \frac{e^{2x}}{4}$$

Back-substitute:

$$I_2 = \frac{x^2 e^{2x}}{2} - \left(\frac{xe^{2x}}{2} - \frac{e^{2x}}{4}\right) = \frac{x^2 e^{2x}}{2} - \frac{xe^{2x}}{2} + \frac{e^{2x}}{4}$$

$$I_3 = \frac{x^3 e^{2x}}{2} - \frac{3}{2}\left(\frac{x^2 e^{2x}}{2} - \frac{xe^{2x}}{2} + \frac{e^{2x}}{4}\right)$$

$$= \frac{x^3 e^{2x}}{2} - \frac{3x^2 e^{2x}}{4} + \frac{3xe^{2x}}{4} - \frac{3e^{2x}}{8} + C$$

Factor out $e^{2x}$:

$$= e^{2x}\left(\frac{x^3}{2} - \frac{3x^2}{4} + \frac{3x}{4} - \frac{3}{8}\right) + C$$



**Solution (Tabular Method):**

| Differentiate | Sign | Integrate           |
| ------------- | ---- | ------------------- |
| $x^3$         | $+$  | $\frac{e^{2x}}{2}$  |
| $3x^2$        | $-$  | $\frac{e^{2x}}{4}$  |
| $6x$          | $+$  | $\frac{e^{2x}}{8}$  |
| $6$           | $-$  | $\frac{e^{2x}}{16}$ |
| $0$           |      |                     |

Result: $$x^3 \cdot \frac{e^{2x}}{2} - 3x^2 \cdot \frac{e^{2x}}{4} + 6x \cdot \frac{e^{2x}}{8} - 6 \cdot \frac{e^{2x}}{16}$$

$$= \frac{x^3e^{2x}}{2} - \frac{3x^2e^{2x}}{4} + \frac{3xe^{2x}}{4} - \frac{3e^{2x}}{8} + C$$ ✓

---

**Example 5.1.2:** Evaluate $\int x^4 e^{-x}dx$

**Solution (Tabular Method):**

| Differentiate | Sign | Integrate |
| ------------- | ---- | --------- |
| $x^4$         | $+$  | $-e^{-x}$ |
| $4x^3$        | $-$  | $+e^{-x}$ |
| $12x^2$       | $+$  | $-e^{-x}$ |
| $24x$         | $-$  | $+e^{-x}$ |
| $24$          | $+$  | $-e^{-x}$ |
| $0$           |      |           |

Result: $$-x^4e^{-x} - 4x^3e^{-x} - 12x^2e^{-x} - 24xe^{-x} - 24e^{-x} + C$$

$$= -e^{-x}(x^4 + 4x^3 + 12x^2 + 24x + 24) + C$$

---

#### 5.2 Gaussian-Type Integrals

**Strategy for $\int x^{2n+1}e^{-x^2}dx$:**

1. Substitute $u = -x^2$, so $du = -2x\,dx$
2. This transforms to $-\frac{1}{2}\int u^n e^u du$
3. Apply polynomial-exponential reduction

**General Pattern:** The result is always $-\frac{e^{-x^2}}{2}P_n(x^2)$ where $P_n$ is a polynomial of degree $n$.

---

**Example 5.2.1:** Evaluate $\int x^3 e^{-x^2}dx$

**Solution:**

Let $u = -x^2$, then $du = -2x\,dx$, so $x\,dx = -\frac{1}{2}du$

Also, $x^2 = -u$

$$\int x^3 e^{-x^2}dx = \int x^2 \cdot e^{-x^2} \cdot x\,dx = \int (-u) \cdot e^u \cdot \left(-\frac{1}{2}du\right)$$

$$= \frac{1}{2}\int u e^u du$$

Integration by parts: $u$ (the variable), $dv = e^u du$: $du = du$, $v = e^u$

$$= \frac{1}{2}(ue^u - \int e^u du) = \frac{1}{2}(ue^u - e^u) + C$$

$$= \frac{e^u(u-1)}{2} + C$$

Substitute back $u = -x^2$:

$$= \frac{e^{-x^2}(-x^2-1)}{2} + C = -\frac{e^{-x^2}(x^2+1)}{2} + C$$

---

**Example 5.2.2:** Evaluate $\int x^5 e^{-x^2}dx$

**Solution:**

Let $u = -x^2$, then $x^4 = u^2$ and $x\,dx = -\frac{1}{2}du$

$$\int x^5 e^{-x^2}dx = \int x^4 \cdot e^{-x^2} \cdot x\,dx = \int u^2 \cdot e^u \cdot \left(-\frac{1}{2}du\right)$$

$$= -\frac{1}{2}\int u^2 e^u du$$

Use tabular method:

| Differentiate | Sign | Integrate |
| ------------- | ---- | --------- |
| $u^2$         | $+$  | $e^u$     |
| $2u$          | $-$  | $e^u$     |
| $2$           | $+$  | $e^u$     |
| $0$           |      |           |

$$\int u^2 e^u du = u^2 e^u - 2ue^u + 2e^u + C = e^u(u^2 - 2u + 2) + C$$

Therefore:

$$-\frac{1}{2}\int u^2 e^u du = -\frac{e^u(u^2-2u+2)}{2} + C$$

Substitute back $u = -x^2$:

$$= -\frac{e^{-x^2}((-x^2)^2 - 2(-x^2) + 2)}{2} + C$$

$$= -\frac{e^{-x^2}(x^4 + 2x^2 + 2)}{2} + C$$

---

**General Reduction Pattern:**

For $\int x^{2n+1}e^{-x^2}dx$, let $u = -x^2$:

$$\int x^{2n+1}e^{-x^2}dx = -\frac{1}{2}\int u^n e^u du$$

Using the reduction formula for $\int u^n e^u du = e^u(u^n - nu^{n-1} + n(n-1)u^{n-2} - \cdots + (-1)^n n!)$:

$$= -\frac{e^{-x^2}}{2}\sum_{k=0}^n (-1)^{n-k}\frac{n!}{k!}(-x^2)^k + C$$

$$= -\frac{e^{-x^2}}{2}\sum_{k=0}^n (-1)^{n-k+k}\frac{n!}{k!}x^{2k} + C$$

$$= -\frac{e^{-x^2}}{2}\sum_{k=0}^n (-1)^n\frac{n!}{k!}x^{2k} + C$$

---

### 5.3 Fractional Exponent Exponentials

**General Strategy for $\int e^{x^{p/q}}dx$:**

**Step 1:** Rationalize the exponent

- Let $t = x^{1/q}$ (where $q$ is the denominator)
- Then $x = t^q$ and $dx = qt^{q-1}dt$
- So $x^{p/q} = (t^q)^{p/q} = t^p$

**Step 2:** Transform the integral $$\int e^{x^{p/q}}dx = \int e^{t^p} \cdot qt^{q-1}dt$$

**Step 3:** Evaluate based on $p$:

- If $p = 1$: Direct exponential-polynomial integration
- If $p > 1$: Generally non-elementary (elliptic-type)

---

**Example 5.3.1:** Evaluate $\int e^{x^{1/3}}dx$

**Solution:**

Here $p/q = 1/3$, so $p = 1$, $q = 3$.

Let $t = x^{1/3}$, so $x = t^3$ and $dx = 3t^2 dt$

$$\int e^{x^{1/3}}dx = \int e^t \cdot 3t^2 dt = 3\int t^2 e^t dt$$

Use tabular method:

| Differentiate | Sign | Integrate |
| ------------- | ---- | --------- |
| $t^2$         | $+$  | $e^t$     |
| $2t$          | $-$  | $e^t$     |
| $2$           | $+$  | $e^t$     |
| $0$           |      |           |

$$\int t^2 e^t dt = t^2 e^t - 2te^t + 2e^t + C = e^t(t^2 - 2t + 2) + C$$

Therefore:

$$3\int t^2 e^t dt = 3e^t(t^2 - 2t + 2) + C$$

Substitute back $t = x^{1/3}$:

$$= 3e^{x^{1/3}}((x^{1/3})^2 - 2x^{1/3} + 2) + C$$

$$= 3e^{x^{1/3}}(x^{2/3} - 2x^{1/3} + 2) + C$$

---

**Example 5.3.2:** Evaluate $\int e^{\sqrt{x}}dx$

**Solution:**

Here we have $x^{1/2}$, so let $t = \sqrt{x}$.

Then $x = t^2$ and $dx = 2t, dt$

$$\int e^{\sqrt{x}}dx = \int e^t \cdot 2t \, dt = 2\int te^t dt$$

Integration by parts: $u = t$, $dv = e^t dt$, $du = dt$, $v = e^t$

$$= 2(te^t - \int e^t dt) = 2(te^t - e^t) + C$$

$$= 2e^t(t-1) + C$$

Substitute back $t = \sqrt{x}$:

$$= 2e^{\sqrt{x}}(\sqrt{x}-1) + C$$

---

## 6. Exponential $\times$ Trigonometric

### 6.1 Basic Forms: $\int e^{Ax}\sin(Bx)dx$ and $\int e^{Ax}\cos(Bx)dx$

These integrals arise frequently in applications (differential equations, Fourier analysis, signal processing). They require either:

1. **Two applications of integration by parts** (traditional method)
2. **Complex exponentials** (Euler's formula method)

------

**Method 1: Double Integration by Parts**

**Derivation for $I = \int e^{Ax}\sin(Bx)dx$:**

First IBP: Let $u = \sin(Bx)$, $dv = e^{Ax}dx$

- $du = B\cos(Bx)dx$
- $v = \frac{e^{Ax}}{A}$

$$I = \frac{e^{Ax}\sin(Bx)}{A} - \frac{B}{A}\int e^{Ax}\cos(Bx)dx$$

Let $J = \int e^{Ax}\cos(Bx)dx$. Then:

$$I = \frac{e^{Ax}\sin(Bx)}{A} - \frac{B}{A}J \quad \cdots (1)$$

Second IBP on $J$: Let $u = \cos(Bx)$, $dv = e^{Ax}dx$

- $du = -B\sin(Bx)dx$
- $v = \frac{e^{Ax}}{A}$

$$J = \frac{e^{Ax}\cos(Bx)}{A} + \frac{B}{A}\int e^{Ax}\sin(Bx)dx$$

$$J = \frac{e^{Ax}\cos(Bx)}{A} + \frac{B}{A}I \quad \cdots (2)$$

Now solve the system of equations (1) and (2):

From (1): $AI = e^{Ax}\sin(Bx) - BJ$

From (2): $AJ = e^{Ax}\cos(Bx) + BI$

Multiply (2) by $B$: $ABJ = Be^{Ax}\cos(Bx) + B^2I$

Substitute into the first equation:

$$AI = e^{Ax}\sin(Bx) - Be^{Ax}\cos(Bx) - B^2I$$

$$AI + B^2I = e^{Ax}(A\sin(Bx) - B\cos(Bx))$$

$$(A^2+B^2)I = Ae^{Ax}\sin(Bx) - Be^{Ax}\cos(Bx)$$

$$\boxed{\int e^{Ax}\sin(Bx)dx = \frac{e^{Ax}(A\sin(Bx) - B\cos(Bx))}{A^2+B^2} + C}$$

$$\boxed{\int e^{Ax}\cos(Bx)dx = \frac{e^{Ax}(A\cos(Bx) + B\sin(Bx))}{A^2+B^2} + C}$$

------

**Method 2: Complex Exponentials (Euler's Formula)**

This method is more systematic and less prone to algebraic errors. It leverages the beautiful relationship: $$e^{i\theta} = \cos\theta + i\sin\theta$$

Consider the complex integral:

$$K = \int e^{Ax} \cdot e^{iBx}dx = \int e^{(A+iB)x}dx$$

This is straightforward:

$$K = \frac{e^{(A+iB)x}}{A+iB} + C_{\text{complex}}$$

Now rationalize the denominator by multiplying by the conjugate:

$$\frac{1}{A+iB} = \frac{A-iB}{(A+iB)(A-iB)} = \frac{A-iB}{A^2+B^2}$$

Therefore:

$$K = \frac{(A-iB)e^{(A+iB)x}}{A^2+B^2} + C_{\text{complex}}$$

$$= \frac{(A-iB)e^{Ax}e^{iBx}}{A^2+B^2} + C_{\text{complex}}$$

$$= \frac{(A-iB)e^{Ax}(\cos(Bx) + i\sin(Bx))}{A^2+B^2} + C_{\text{complex}}$$

Expand:

$$= \frac{e^{Ax}}{A^2+B^2}[(A\cos(Bx) + B\sin(Bx)) + i(A\sin(Bx) - B\cos(Bx))] + C_{\text{complex}}$$

But also:

$$K = \int e^{Ax}(\cos(Bx) + i\sin(Bx))dx = \int e^{Ax}\cos(Bx)dx + i\int e^{Ax}\sin(Bx)dx$$

$$= J + iI$$

Comparing real and imaginary parts:

$$I = \int e^{Ax}\sin(Bx)dx = \frac{e^{Ax}(A\sin(Bx) - B\cos(Bx))}{A^2+B^2} + C$$

$$J = \int e^{Ax}\cos(Bx)dx = \frac{e^{Ax}(A\cos(Bx) + B\sin(Bx))}{A^2+B^2} + C$$

------

**Example 6.1.1:** Evaluate $\int e^{3x}\sin(2x)dx$

**Solution (Using Formula):**

Here $A = 3$, $B = 2$, so $A^2 + B^2 = 9 + 4 = 13$

$$\int e^{3x}\sin(2x)dx = \frac{e^{3x}(3\sin(2x) - 2\cos(2x))}{13} + C$$

------

**Example 6.1.2:** Evaluate $\int e^{-x}\cos(3x)dx$

**Solution:**

Here $A = -1$, $B = 3$, so $A^2 + B^2 = 1 + 9 = 10$

$$\int e^{-x}\cos(3x)dx = \frac{e^{-x}(-\cos(3x) + 3\sin(3x))}{10} + C$$

$$= \frac{e^{-x}(3\sin(3x) - \cos(3x))}{10} + C$$

------

### 6.2 Product-to-Sum Reduction

**Strategy:** When you have products like $\sin(Ax)\cos(Bx)$, use product-to-sum identities:

$$\sin(A)\cos(B) = \frac{1}{2}[\sin(A+B) + \sin(A-B)]$$ 

$$\sin(A)\sin(B) = \frac{1}{2}[\cos(A-B) - \cos(A+B)]$$ 

$$\cos(A)\cos(B) = \frac{1}{2}[\cos(A+B) + \cos(A-B)]$$

After applying these identities, integrate each term using the standard formulas.

------

**Example 6.2.1:** Evaluate $\int e^{2x}\sin(3x)\cos(x)dx$

**Solution:**

First, use the product-to-sum identity for $\sin(3x)\cos(x)$:

$$\sin(3x)\cos(x) = \frac{1}{2}[\sin(3x+x) + \sin(3x-x)] = \frac{1}{2}[\sin(4x) + \sin(2x)]$$

Therefore:

$$\int e^{2x}\sin(3x)\cos(x)dx = \frac{1}{2}\int e^{2x}\sin(4x)dx + \frac{1}{2}\int e^{2x}\sin(2x)dx$$

Apply the standard formula to each integral:

**First integral:** $A = 2$, $B = 4$, $A^2 + B^2 = 4 + 16 = 20$

$$\int e^{2x}\sin(4x)dx = \frac{e^{2x}(2\sin(4x) - 4\cos(4x))}{20} = \frac{e^{2x}(\sin(4x) - 2\cos(4x))}{10}$$

**Second integral:** $A = 2$, $B = 2$, $A^2 + B^2 = 8$

$$\int e^{2x}\sin(2x)dx = \frac{e^{2x}(2\sin(2x) - 2\cos(2x))}{8} = \frac{e^{2x}(\sin(2x) - \cos(2x))}{4}$$

Combine:

$$= \frac{1}{2} \cdot \frac{e^{2x}(\sin(4x) - 2\cos(4x))}{10} + \frac{1}{2} \cdot \frac{e^{2x}(\sin(2x) - \cos(2x))}{4} + C$$

$$= \frac{e^{2x}(\sin(4x) - 2\cos(4x))}{20} + \frac{e^{2x}(\sin(2x) - \cos(2x))}{8} + C$$

------

**Example 6.2.2:** Evaluate $\int e^x\sin(x)\sin(2x)dx$

**Solution:**

Use the product-to-sum identity for $\sin(x)\sin(2x)$:

$$\sin(x)\sin(2x) = \frac{1}{2}[\cos(x-2x) - \cos(x+2x)] = \frac{1}{2}[\cos(-x) - \cos(3x)]$$

$$= \frac{1}{2}[\cos(x) - \cos(3x)]$$

Therefore:

$$\int e^x\sin(x)\sin(2x)dx = \frac{1}{2}\int e^x\cos(x)dx - \frac{1}{2}\int e^x\cos(3x)dx$$

**First integral:** $A = 1$, $B = 1$, $A^2 + B^2 = 2$

$$\int e^x\cos(x)dx = \frac{e^x(\cos(x) + \sin(x))}{2}$$

**Second integral:** $A = 1$, $B = 3$, $A^2 + B^2 = 10$

$$\int e^x\cos(3x)dx = \frac{e^x(\cos(3x) + 3\sin(3x))}{10}$$

Combine:

$$= \frac{1}{2} \cdot \frac{e^x(\cos(x) + \sin(x))}{2} - \frac{1}{2} \cdot \frac{e^x(\cos(3x) + 3\sin(3x))}{10} + C$$

$$= \frac{e^x(\cos(x) + \sin(x))}{4} - \frac{e^x(\cos(3x) + 3\sin(3x))}{20} + C$$

------

**Example 6.2.3:** Evaluate $\int e^{-x}\cos(2x)\cos(x)dx$

**Solution:**

Use $\cos(2x)\cos(x) = \frac{1}{2}[\cos(3x) + \cos(x)]$

$$\int e^{-x}\cos(2x)\cos(x)dx = \frac{1}{2}\int e^{-x}\cos(3x)dx + \frac{1}{2}\int e^{-x}\cos(x)dx$$

**First integral:** $A = -1$, $B = 3$, $A^2 + B^2 = 10$

$$\int e^{-x}\cos(3x)dx = \frac{e^{-x}(-\cos(3x) + 3\sin(3x))}{10}$$

**Second integral:** $A = -1$, $B = 1$, $A^2 + B^2 = 2$

$$\int e^{-x}\cos(x)dx = \frac{e^{-x}(-\cos(x) + \sin(x))}{2}$$

Combine:

$$= \frac{1}{2} \cdot \frac{e^{-x}(3\sin(3x) - \cos(3x))}{10} + \frac{1}{2} \cdot \frac{e^{-x}(\sin(x) - \cos(x))}{2} + C$$

$$= \frac{e^{-x}(3\sin(3x) - \cos(3x))}{20} + \frac{e^{-x}(\sin(x) - \cos(x))}{4} + C$$

------

### 6.3 Mixed Trigonometric-Hyperbolic

When mixing trigonometric and hyperbolic functions, convert everything to exponentials. Recall:

$$\sinh(x) = \frac{e^x - e^{-x}}{2}, \quad \cosh(x) = \frac{e^x + e^{-x}}{2}$$

$$\sin(x) = \frac{e^{ix} - e^{-ix}}{2i}, \quad \cos(x) = \frac{e^{ix} + e^{-ix}}{2}$$

After conversion, the problem reduces to exponential-trigonometric integrals.

------

**Example 6.3.1:** Evaluate $\int \sin(x)\sinh(x)dx$

**Solution:**

Convert to exponentials:

$$\sinh(x) = \frac{e^x - e^{-x}}{2}$$

$$\int \sin(x)\sinh(x)dx = \int \sin(x) \cdot \frac{e^x - e^{-x}}{2}dx$$

$$= \frac{1}{2}\int e^x\sin(x)dx - \frac{1}{2}\int e^{-x}\sin(x)dx$$

**First integral:** $A = 1$, $B = 1$, $A^2 + B^2 = 2$

$$\int e^x\sin(x)dx = \frac{e^x(\sin(x) - \cos(x))}{2}$$

**Second integral:** $A = -1$, $B = 1$, $A^2 + B^2 = 2$

$$\int e^{-x}\sin(x)dx = \frac{e^{-x}(-\sin(x) - \cos(x))}{2} = -\frac{e^{-x}(\sin(x) + \cos(x))}{2}$$

Combine:

$$= \frac{1}{2} \cdot \frac{e^x(\sin(x) - \cos(x))}{2} - \frac{1}{2} \cdot \left(-\frac{e^{-x}(\sin(x) + \cos(x))}{2}\right) + C$$

$$= \frac{e^x(\sin(x) - \cos(x))}{4} + \frac{e^{-x}(\sin(x) + \cos(x))}{4} + C$$

$$= \frac{1}{4}[e^x(\sin(x) - \cos(x)) + e^{-x}(\sin(x) + \cos(x))] + C$$

Factor by terms:

$$= \frac{1}{4}[\sin(x)(e^x + e^{-x}) - \cos(x)(e^x - e^{-x})] + C$$

$$= \frac{1}{2}[\sin(x)\cosh(x) - \cos(x)\sinh(x)] + C$$

------

**Example 6.3.2:** Evaluate $\int \cos(x)\cosh(x)dx$

**Solution:**

$$\int \cos(x)\cosh(x)dx = \int \cos(x) \cdot \frac{e^x + e^{-x}}{2}dx$$

$$= \frac{1}{2}\int e^x\cos(x)dx + \frac{1}{2}\int e^{-x}\cos(x)dx$$

**First integral:** $A = 1$, $B = 1$

$$\int e^x\cos(x)dx = \frac{e^x(\cos(x) + \sin(x))}{2}$$

**Second integral:** $A = -1$, $B = 1$

$$\int e^{-x}\cos(x)dx = \frac{e^{-x}(-\cos(x) + \sin(x))}{2} = \frac{e^{-x}(\sin(x) - \cos(x))}{2}$$

Combine:

$$= \frac{1}{2} \cdot \frac{e^x(\cos(x) + \sin(x))}{2} + \frac{1}{2} \cdot \frac{e^{-x}(\sin(x) - \cos(x))}{2} + C$$

$$= \frac{e^x(\cos(x) + \sin(x))}{4} + \frac{e^{-x}(\sin(x) - \cos(x))}{4} + C$$

$$= \frac{1}{4}[e^x(\cos(x) + \sin(x)) + e^{-x}(\sin(x) - \cos(x))] + C$$

Factor:

$$= \frac{1}{4}[\sin(x)(e^x + e^{-x}) + \cos(x)(e^x - e^{-x})] + C$$

$$= \frac{1}{2}[\sin(x)\cosh(x) + \cos(x)\sinh(x)] + C$$

------

**Example 6.3.3:** Evaluate $\int \sin(x)\cosh(2x)dx$

**Solution:**

$$\int \sin(x)\cosh(2x)dx = \int \sin(x) \cdot \frac{e^{2x} + e^{-2x}}{2}dx$$

$$= \frac{1}{2}\int e^{2x}\sin(x)dx + \frac{1}{2}\int e^{-2x}\sin(x)dx$$

**First integral:** $A = 2$, $B = 1$, $A^2 + B^2 = 5$

$$\int e^{2x}\sin(x)dx = \frac{e^{2x}(2\sin(x) - \cos(x))}{5}$$

**Second integral:** $A = -2$, $B = 1$, $A^2 + B^2 = 5$

$$\int e^{-2x}\sin(x)dx = \frac{e^{-2x}(-2\sin(x) - \cos(x))}{5}$$

Combine:

$$= \frac{1}{2} \cdot \frac{e^{2x}(2\sin(x) - \cos(x))}{5} + \frac{1}{2} \cdot \frac{e^{-2x}(-2\sin(x) - \cos(x))}{5} + C$$

$$= \frac{e^{2x}(2\sin(x) - \cos(x))}{10} - \frac{e^{-2x}(2\sin(x) + \cos(x))}{10} + C$$

------

**Example 6.3.4:** Evaluate $\int \cos(3x)\sinh(x)dx$

**Solution:**

$$\int \cos(3x)\sinh(x)dx = \int \cos(3x) \cdot \frac{e^x - e^{-x}}{2}dx$$

$$= \frac{1}{2}\int e^x\cos(3x)dx - \frac{1}{2}\int e^{-x}\cos(3x)dx$$

**First integral:** $A = 1$, $B = 3$, $A^2 + B^2 = 10$

$$\int e^x\cos(3x)dx = \frac{e^x(\cos(3x) + 3\sin(3x))}{10}$$

**Second integral:** $A = -1$, $B = 3$, $A^2 + B^2 = 10$

$$\int e^{-x}\cos(3x)dx = \frac{e^{-x}(-\cos(3x) + 3\sin(3x))}{10}$$

Combine:

$$= \frac{1}{2} \cdot \frac{e^x(\cos(3x) + 3\sin(3x))}{10} - \frac{1}{2} \cdot \frac{e^{-x}(3\sin(3x) - \cos(3x))}{10} + C$$

$$= \frac{e^x(\cos(3x) + 3\sin(3x))}{20} - \frac{e^{-x}(3\sin(3x) - \cos(3x))}{20} + C$$

$$= \frac{1}{20}[e^x(\cos(3x) + 3\sin(3x)) - e^{-x}(3\sin(3x) - \cos(3x))] + C$$

$$= \frac{1}{10}[\cos(3x)\cosh(x) + 3\sin(3x)\sinh(x)] + C$$

### 7. Polynomial × Trigonometric

When polynomial functions multiply trigonometric functions, we also need systematic reduction formulas. Unlike polynomial × exponential (where one reduction formula suffices), polynomial × trigonometric integrals require a coupled system because differentiating sine gives cosine and vice versa. Moreover, unlike exponential $\times$ trigomimetric (which coexist well in complex), no magic relations underly this couple.

------

### 7.1 Basic Mutual Reduction System

**Define:** $$I_n = \int x^n \sin(bx) \ \, dx$$ $$J_n = \int x^n \cos(bx) \, dx$$

These are inherently coupled because:

- Differentiating $\sin(bx)$ gives $b\cos(bx)$
- Differentiating $\cos(bx)$ gives $-b\sin(bx)$

**First-Order Reduction (Coupled Formulas):**

For $I_n = \int x^n \sin(bx) \ \, dx$, use IBP with $u = x^n$, $dv = \sin(bx)dx$:

- $du = nx^{n-1}dx$
- $v = -\frac{\cos(bx)}{b}$

$$I_n = -\frac{x^n \cos(bx)}{b} + \int \frac{\cos(bx)}{b} \cdot nx^{n-1}dx$$

$$\boxed{I_n = -\frac{x^n \cos(bx)}{b} + \frac{n}{b}J_{n-1}}$$

Similarly, for $J_n = \int x^n \cos(bx) \ \, dx$, use IBP with $u = x^n$, $dv = \cos(bx)dx$:

- $du = nx^{n-1}dx$
- $v = \frac{\sin(bx)}{b}$

$$J_n = \frac{x^n \sin(bx)}{b} - \int \frac{\sin(bx)}{b} \cdot nx^{n-1}dx$$

$$\boxed{J_n = \frac{x^n \sin(bx)}{b} - \frac{n}{b}I_{n-1}}$$

**The Problem with First-Order Reduction:**

To compute $I_n$, we need $J_{n-1}$. To compute $J_{n-1}$, we need $I_{n-2}$.

This back-and-forth is cumbersome for large $n$. We need a better approach.

------

### 7.2 Complete Second-Order Reduction

We can eliminate the mutual dependence by substituting one formula into the other, creating a direct reduction formula that only involves integrals of the same type.

**Deriving Second-Order Reduction for $I_n$:**

From the coupled formulas: $$I_n = -\frac{x^n \cos(bx)}{b} + \frac{n}{b}J_{n-1}$$

We need to express $J_{n-1}$ without referring to $I$. Use the formula for $J_{n-1}$:

$$J_{n-1} = \frac{x^{n-1}\sin(bx)}{b} - \frac{n-1}{b}I_{n-2}$$

Substitute this into the expression for $I_n$:

$$I_n = -\frac{x^n \cos(bx)}{b} + \frac{n}{b}\left(\frac{x^{n-1}\sin(bx)}{b} - \frac{n-1}{b}I_{n-2}\right)$$

$$= -\frac{x^n \cos(bx)}{b} + \frac{nx^{n-1}\sin(bx)}{b^2} - \frac{n(n-1)}{b^2}I_{n-2}$$

$$\boxed{I_n = \frac{nx^{n-1}\sin(bx)}{b^2} - \frac{x^n \cos(bx)}{b} - \frac{n(n-1)}{b^2}I_{n-2}}$$

**Similarly, for $J_n$:**

From $J_n = \frac{x^n \sin(bx)}{b} - \frac{n}{b}I_{n-1}$ and $I_{n-1} = -\frac{x^{n-1}\cos(bx)}{b} + \frac{n-1}{b}J_{n-2}$:

$$J_n = \frac{x^n \sin(bx)}{b} - \frac{n}{b}\left(-\frac{x^{n-1}\cos(bx)}{b} + \frac{n-1}{b}J_{n-2}\right)$$

$$= \frac{x^n \sin(bx)}{b} + \frac{nx^{n-1}\cos(bx)}{b^2} - \frac{n(n-1)}{b^2}J_{n-2}$$

$$\boxed{J_n = \frac{nx^{n-1}\cos(bx)}{b^2} + \frac{x^n \sin(bx)}{b} - \frac{n(n-1)}{b^2}J_{n-2}}$$

**Base Cases:** $$I_0 = \int \sin(bx)dx = -\frac{\cos(bx)}{b} + C$$ $$I_1 = \int x\sin(bx)dx = -\frac{x\cos(bx)}{b} + \frac{\sin(bx)}{b^2} + C$$

$$J_0 = \int \cos(bx)dx = \frac{\sin(bx)}{b} + C$$ $$J_1 = \int x\cos(bx)dx = \frac{x\sin(bx)}{b} + \frac{\cos(bx)}{b^2} + C$$

------

**Example 7.2.1:** Evaluate $\int x^3 \sin(2x) \ \, dx$

**Solution:**

We need $I_3$ with $b = 2$.

Using the reduction formula: $$I_3 = \frac{3x^2\sin(2x)}{4} - \frac{x^3\cos(2x)}{2} - \frac{3 \cdot 2}{4}I_1$$

$$= \frac{3x^2\sin(2x)}{4} - \frac{x^3\cos(2x)}{2} - \frac{3}{2}I_1$$

Now compute $I_1$: $$I_1 = \int x\sin(2x)dx = -\frac{x\cos(2x)}{2} + \frac{\sin(2x)}{4}$$

Substitute back: $$I_3 = \frac{3x^2\sin(2x)}{4} - \frac{x^3\cos(2x)}{2} - \frac{3}{2}\left(-\frac{x\cos(2x)}{2} + \frac{\sin(2x)}{4}\right)$$

$$= -\frac{x^3\cos(2x)}{2} + \frac{3x^2\sin(2x)}{4} + \frac{3x\cos(2x)}{4} - \frac{3\sin(2x)}{8} + C$$

------

**Example 7.2.2:** Evaluate $\int x^4 \cos(x) \ \, dx$

**Solution:**

We need $J_4$ with $b = 1$.

$$J_4 = 4x^3\cos(x) + x^4\sin(x) - 12J_2$$

Now compute $J_2$: $$J_2 = 2x\cos(x) + x^2\sin(x) - 2J_0$$

$$J_0 = \sin(x)$$

So: $$J_2 = 2x\cos(x) + x^2\sin(x) - 2\sin(x)$$

Substitute back into $J_4$: $$J_4 = 4x^3\cos(x) + x^4\sin(x) - 12[2x\cos(x) + x^2\sin(x) - 2\sin(x)]$$

$$= 4x^3\cos(x) + x^4\sin(x) - 24x\cos(x) - 12x^2\sin(x) + 24\sin(x) + C$$

------

**Example 7.2.3:** Evaluate $\int x^2 \sin(3x) \ \, dx$

**Solution:**

We need $I_2$ with $b = 3$.

$$I_2 = \frac{2x\sin(3x)}{9} - \frac{x^2\cos(3x)}{3} - \frac{2}{9}I_0$$

$$I_0 = -\frac{\cos(3x)}{3}$$

Therefore: $$I_2 = \frac{2x\sin(3x)}{9} - \frac{x^2\cos(3x)}{3} - \frac{2}{9} \cdot \left(-\frac{\cos(3x)}{3}\right)$$

$$= \frac{2x\sin(3x)}{9} - \frac{x^2\cos(3x)}{3} + \frac{2\cos(3x)}{27} + C$$

------

### 7.3 Mixed Sine-Cosine with Polynomial

When the integrand contains products like $x^n\sin(ax)\cos(bx)$, our strategy:

1. Apply product-to-sum identity to simplify the trigonometric product
2. Distribute the polynomial factor
3. Apply the reduction formulas from Section 5.2 to each term

------

**Example 7.3.1:** Evaluate $\int x^2 \sin(x)\cos(x) \ \, dx$

**Solution:**

**Step 1:** Use the identity $\sin(x)\cos(x) = \frac{1}{2}\sin(2x)$

$$\int x^2 \sin(x)\cos(x) \ \, dx = \frac{1}{2}\int x^2\sin(2x)dx$$

**Step 2:** This is $\frac{1}{2}I_2$ with $b = 2$.

Using the reduction formula: $$I_2 = \frac{2x\sin(2x)}{4} - \frac{x^2\cos(2x)}{2} - \frac{2}{4}I_0$$

$$= \frac{x\sin(2x)}{2} - \frac{x^2\cos(2x)}{2} - \frac{1}{2}I_0$$

$$I_0 = -\frac{\cos(2x)}{2}$$

Therefore: $$I_2 = \frac{x\sin(2x)}{2} - \frac{x^2\cos(2x)}{2} + \frac{\cos(2x)}{4}$$

**Step 3:** Multiply by $\frac{1}{2}$:

$$\frac{1}{2}I_2 = \frac{x\sin(2x)}{4} - \frac{x^2\cos(2x)}{4} + \frac{\cos(2x)}{8} + C$$

------

**Example 7.3.2:** Evaluate $\int x\sin(2x)\sin(3x) \ \, dx$

**Solution:**

**Step 1:** Use the product-to-sum identity: $$\sin(2x)\sin(3x) = \frac{1}{2}[\cos(2x-3x) - \cos(2x+3x)]$$

$$= \frac{1}{2}[\cos(-x) - \cos(5x)] = \frac{1}{2}[\cos(x) - \cos(5x)]$$

**Step 2:** Therefore: $$\int x\sin(2x)\sin(3x) \ \, dx = \frac{1}{2}\int x\cos(x)dx - \frac{1}{2}\int x\cos(5x)dx$$

$$= \frac{1}{2}J_1(b=1) - \frac{1}{2}J_1(b=5)$$

**Step 3:** Compute each term:

For $J_1$ with $b = 1$: $$\int x\cos(x)dx = x\sin(x) + \cos(x)$$

For $J_1$ with $b = 5$: $$\int x\cos(5x)dx = \frac{x\sin(5x)}{5} + \frac{\cos(5x)}{25}$$

**Step 4:** Combine: $$= \frac{1}{2}[x\sin(x) + \cos(x)] - \frac{1}{2}\left[\frac{x\sin(5x)}{5} + \frac{\cos(5x)}{25}\right] + C$$

$$= \frac{x\sin(x)}{2} + \frac{\cos(x)}{2} - \frac{x\sin(5x)}{10} - \frac{\cos(5x)}{50} + C$$

------

**Example 7.3.3:** Evaluate $\int x^2\cos(x)\cos(2x) \ \, dx$

**Solution:**

**Step 1:** Use the product-to-sum identity: $$\cos(x)\cos(2x) = \frac{1}{2}[\cos(x-2x) + \cos(x+2x)]$$

$$= \frac{1}{2}[\cos(-x) + \cos(3x)] = \frac{1}{2}[\cos(x) + \cos(3x)]$$

**Step 2:** Therefore: $$\int x^2\cos(x)\cos(2x) \ \, dx = \frac{1}{2}\int x^2\cos(x)dx + \frac{1}{2}\int x^2\cos(3x)dx$$

$$= \frac{1}{2}J_2(b=1) + \frac{1}{2}J_2(b=3)$$

**Step 3:** Compute $J_2$ with $b = 1$:

$$J_2 = 2x\cos(x) + x^2\sin(x) - 2J_0$$

$$J_0 = \sin(x)$$

$$J_2 = 2x\cos(x) + x^2\sin(x) - 2\sin(x)$$

**Step 4:** Compute $J_2$ with $b = 3$:

$$J_2 = \frac{2x\cos(3x)}{9} + \frac{x^2\sin(3x)}{3} - \frac{2}{9}J_0$$

$$J_0 = \frac{\sin(3x)}{3}$$

$$J_2 = \frac{2x\cos(3x)}{9} + \frac{x^2\sin(3x)}{3} - \frac{2\sin(3x)}{27}$$

**Step 5:** Combine: $$= \frac{1}{2}[2x\cos(x) + x^2\sin(x) - 2\sin(x)]$$ $$\quad + \frac{1}{2}\left[\frac{2x\cos(3x)}{9} + \frac{x^2\sin(3x)}{3} - \frac{2\sin(3x)}{27}\right] + C$$

$$= x\cos(x) + \frac{x^2\sin(x)}{2} - \sin(x) + \frac{x\cos(3x)}{9} + \frac{x^2\sin(3x)}{6} - \frac{\sin(3x)}{27} + C$$



---



