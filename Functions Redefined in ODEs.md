# Functions Redefined in ODEs

Yuebo Hu, TA of MATH1560J, GC, SJTU

liuyejiang576@sjtu.edu.cn

November, 2025



---

## 1.  Introduction: Defining a Function

When you first learned about the exponential function, you likely encountered it as $a^x$ where $a > 0$. Perhaps you started with integer powers, then rational powers, and finally extended to all real numbers through limits or continuity arguments. Similarly, sine and cosine were probably introduced through the unit circle or right triangle ratios.

But here's a profound question: What is a function?

Is it a formula? A geometric construction? Or something more abstract—a rule that satisfies certain properties?

Many of the most important functions in mathematics can be defined purely through the differential equations they satisfy. This approach is often more fundamental, more natural, and more revealing than traditional approaches, because it describes how a function changes in relation to itself. 

Mathematics often gives us multiple ways to define the "same" object. But what does "same" mean? In rigorous terms, we prove that different constructions yield objects with identical properties—they're **isomorphic** or **equivalent** in a precise sense.

For example, we'll see that:

- The function satisfying $f'(x) = f(x)$ with $f(0) = 1$
- The limit $\lim_{n \to \infty} (1 + 1/n)^n$
- The infinite series $\sum_{k=0}^{\infty} \frac{1}{k!}$

all define the “same” function because we can prove they have identical values at every point. The ODE definition is often the most elegant because it captures the function's essence: exponential growth is characterized by the property that the rate of growth equals the current value.

------

## 2. The Exponential Function via $f' - f = 0$

### 2.1 Verification

Let's begin with perhaps the most important function in all of mathematics. We define the exponential function $\exp(x)$ as the **unique solution** to the initial value problem:

$$f'(x) = f(x), \quad f(0) = 1$$

Let's verify that a solution exists and find it. We'll use the **separation of variables** technique.

Starting with $f'(x) = f(x)$, we rearrange (assuming $f(x) \neq 0$ for now):

$$\frac{f'(x)}{f(x)} = 1$$

Integrate both sides with respect to $x$:

$$\ln|f(x)| = x + C$$

where $C$ is a constant of integration. Exponentiating both sides:

$$|f(x)| = e^{x + C} = e^C \cdot e^x$$

Since we need $f(0) = 1$, we have $|f(0)| = e^C = 1$, which gives $e^C = 1$, so $C = 0$. Also, since $f(0) = 1 > 0$ and $f$ is continuous (as a solution to a continuous ODE), $f(x)$ must remain positive, so we can drop the absolute value:

$$f(x) = e^x$$

What we've shown is that if there's a solution, it must have the form of an exponential. Here we use the definition of $exp$ as the inverse of $ln$.

### 2.2 Connections

Now let's connect our ODE definition to traditional approaches:

#### Connection 1: The Number $e$

We define $e := \exp(1)$, that is, the value of our function at $x = 1$. We can show that:

$$e = \lim_{n \to \infty} \left(1 + \frac{1}{n}\right)^n$$

**Proof sketch using Euler's method**: Consider approximating the solution to $f' = f, f(0) = 1$ on the interval $[0, 1]$ using Euler's method with step size $h = 1/n$.

Euler's method gives us: $y_{k+1} = y_k + h \cdot f'(x_k) = y_k + h \cdot y_k = y_k(1 + h)$

Starting with $y_0 = f(0) = 1$ and taking $n$ steps of size $h = 1/n$ to reach $x = 1$:

$$y_n = y_0 (1 + h)^n = 1 \cdot \left(1 + \frac{1}{n}\right)^n$$

As $n \to \infty$ (equivalently, $h \to 0$), Euler's method converges to the true solution, so:

$$e = \exp(1) = \lim_{n \to \infty} \left(1 + \frac{1}{n}\right)^n$$

#### Connection 2: The Power Series

From the ODE $f'(x) = f(x)$ with $f(0) = 1$, if we assume $f$ has a power series:

$$f(x) = \sum_{k=0}^{\infty} a_k x^k$$

then:

$$f'(x) = \sum_{k=1}^{\infty} k \cdot a_k x^{k-1} = \sum_{k=0}^{\infty} (k+1) a_{k+1} x^k$$

The equation $f'(x) = f(x)$ gives:

$$\sum_{k=0}^{\infty} (k+1) a_{k+1} x^k = \sum_{k=0}^{\infty} a_k x^k$$

Comparing coefficients: $(k+1) a_{k+1} = a_k$, so:

$$a_{k+1} = \frac{a_k}{k+1}$$

With $a_0 = f(0) = 1$, we get:

$$a_1 = \frac{1}{1}, \quad a_2 = \frac{1}{2 \cdot 1}, \quad a_3 = \frac{1}{3 \cdot 2 \cdot 1}, \quad \ldots, \quad a_k = \frac{1}{k!}$$

Therefore:

$$\exp(x) = \sum_{k=0}^{\infty} \frac{x^k}{k!}$$

In particular, $e = \exp(1) = \sum_{k=0}^{\infty} \frac{1}{k!}$.

#### Connection 3: The Natural Logarithm

Define the natural logarithm as:

$$\ln(x) = \int_1^x \frac{1}{t} , dt \quad \text{for } x > 0$$

We can show that $\ln$ and $\exp$ are inverse functions. If $y = \exp(x)$, then $y' = y$, so:

$$\frac{dy}{dx} = y$$

By the chain rule, if $x = \ln(y)$:

$$\frac{dx}{dy} = \frac{1}{dy/dx} = \frac{1}{y}$$

Integrating from $y = 1$ (where $x = 0$ since $\exp(0) = 1$) to $y$:

$$\ln(y) = \int_1^y \frac{1}{t} , dt$$

This confirms that $\ln$ and $\exp$ are inverses.

#### Connection 4: The Derivative Characterization

The ODE definition immediately tells us that $\exp'(0) = \exp(0) = 1$. If we think of $\exp(x)$ as $e^x$ (a power with base $e$), this says:

$$\frac{d}{dx} e^x \bigg|_{x=0} = 1$$

Conversely, we can characterize $e$ as the unique base $a > 0$ such that $\frac{d}{dx} a^x |_{x=0} = 1$.

### 2.3 The General Case

For any constant $k$, the ODE:

$$f'(x) = k f(x), \quad f(0) = A$$

has the solution:

$$f(x) = A \exp(kx)$$

**Verification**: $$f'(x) = A \cdot k \exp(kx) = k \cdot (A \exp(kx)) = k f(x) \quad \checkmark$$ $$f(0) = A \exp(0) = A \cdot 1 = A \quad \checkmark$$

This models exponential growth ($k > 0$) or decay ($k < 0$), appearing everywhere from population dynamics to radioactive decay to compound interest.

### 2.4 Properties

One of the most important properties of the exponential function is:

$$\exp(x + y) = \exp(x) \exp(y)$$

**Proof from the ODE**: Fix $y$ and define $g(x) = \exp(x + y)$. Then:

$$g'(x) = \exp'(x + y) \cdot 1 = \exp(x + y) = g(x)$$

So $g$ satisfies $g'(x) = g(x)$. Also, $g(0) = \exp(y)$.

By uniqueness of solutions to the IVP $f'(x) = f(x), f(0) = c$, we must have:

$$g(x) = \exp(y) \cdot \exp(x)$$

Therefore:

$$\exp(x + y) = \exp(x) \exp(y)$$

From this, we can derive all the power laws:

- $\exp(nx) = \exp(x)^n$ for integer $n$
- $\exp(x/n) = \exp(x)^{1/n}$
- $\exp(rx) = \exp(x)^r$ for rational $r$
- By continuity, $\exp(αx) = \exp(x)^α$ for all real $α$

### 2.5 Complex Extension

We can extend $\exp$ to complex numbers. For purely imaginary input $i\theta$ where $i^2 = -1$:

$$f(x) = \exp(i\theta x)$$  satisfies  $$f'(x) = i\theta \exp(i\theta x) = i\theta \cdot f(x)$$

This is a first-order ODE, but what does it mean? We'll see in the next section.

------

## 3. Trigonometric Functions via $f'' + f = 0$

### 3.1 The Defining ODE

Now we turn to the second-order ODE:

$$f''(x) + f(x) = 0$$

This equation appears everywhere: oscillating springs, pendulums, LC circuits, wave equations. It describes **simple harmonic motion**—systems where the restoring force is proportional to displacement.

We need two linearly independent solutions since this is a second-order ODE. Define:

- $S(x)$: the solution with $S(0) = 0, S'(0) = 1$
- $C(x)$: the solution with $C(0) = 1, C'(0) = 0$

We'll call these the "sine-like" and "cosine-like" functions, though we haven't yet connected them to the unit circle.

### 3.2 Derivative Relations

From the ODE $f'' + f = 0$, we have $f'' = -f$. Let's define $D(x) = S'(x)$ (motivated by the initial condition $S'(0) = 1$). We will now prove that $D$ is identical to $C$.

For $D(x) = S'(x)$: $D'(x) = S''(x) = -S(x)$. $D''(x) = -S'(x) = -D(x)$. Therefore $D'' + D = 0$.

For $C(x)$: By definition, $C'' + C = 0$. Thus, both $D$ and $C$ are solutions to the ODE $f'' + f = 0$:

Now check initial conditions:
- $D(0) = S'(0) = 1$ and $C(0) = 1$ (by definition)
- $D'(0) = S''(0) = -S(0) = 0$ and $C'(0) = 0$ (by definition)

Since $D$ and $C$ satisfy the same second-order linear ODE with the same initial conditions, by the uniqueness theorem for ODEs, we conclude that $D(x) = C(x)$ for all $x$.

With $D = C$ established, we have:
- $S'(x) = D(x) = C(x)$
- $C'(x) = D'(x) = S''(x) = -S(x)$

Thus we obtain the elegant coupled system:

$$\begin{cases} S'(x) = C(x) \\ C'(x) = -S(x) \end{cases}$$

This reveals the beautiful interconnection between these functions: the derivative of $S$ gives $C$, and the derivative of $C$ gives $-S$.

### 3.3 The Conservation Identity

This is where magic happens. Define:

$$E(x) = S(x)^2 + C(x)^2$$

$$E'(x) = 2S(x)S'(x) + 2C(x)C'(x)$$

Using our derivative relations $S' = C$ and $C' = -S$:

$$E'(x) = 2S(x)C(x) + 2C(x)(-S(x)) = 2S(x)C(x) - 2S(x)C(x) = 0$$

So $E(x)$ is constant! Check at $x = 0$:

$$E(0) = S(0)^2 + C(0)^2 = 0^2 + 1^2 = 1$$

Therefore: $$S(x)^2 + C(x)^2 = 1 \,\, \text{for all } x$$

This is the Pythagorean identity, derived purely from the ODE—no circles in sight! Yet the equation $S^2 + C^2 = 1$ defines points on the unit circle. This is our first hint that the ODE definition and geometric definition are the same.

### 3.4 The Existence of $\pi$

Since $S(x)^2 + C(x)^2 = 1$ and both are continuous, and $S(0) = 0, S'(0) = 1 > 0$, the function $S(x)$ is initially increasing. As $x$ increases from 0, $S(x)$ increases from 0.

Can $S(x)$ keep increasing forever? No. Since $S(x)^2 \leq 1$, we have $|S(x)| \leq 1$. So $S$ is bounded.

Also, when $S(x) = 1$, we must have $C(x) = 0$ (from $S^2 + C^2 = 1$). At such a point:

$$S'(x) = C(x) = 0$$

So $S$ has a critical point when it reaches 1.

We define: $$\frac{\pi}{2} := \text{smallest positive } x \text{ such that } S(x) = 1$$

At this point, $S(\pi/2) = 1$ and $C(\pi/2) = 0$.

This gives us $\pi$ purely from analysis—again, no geometry needed.

### 3.5 Phase Shifts and Periodicity

Consider the function $g(x) = S(x + \pi/2)$. What ODE does it satisfy?

$$g''(x) = S''(x + \pi/2) = -S(x + \pi/2) = -g(x)$$

So $g'' + g = 0$. What are its initial conditions?

$$g(0) = S(\pi/2) = 1$$ $$g'(0) = S'(\pi/2) = C(\pi/2) = 0$$

These are exactly the initial conditions for $C(x)$ .By uniqueness of solutions to the IVP:

$$S(x + \pi/2) = C(x)$$

Similarly, we can show:

$$C(x + \pi/2) = -S(x)$$

**Verification**: If $h(x) = C(x + \pi/2)$, then $h''+ h = 0$, and: $$h(0) = C(\pi/2) = 0, \quad h'(0) = C'(\pi/2) = -S(\pi/2) = -1$$

So $h(x) = -S(x)$ by uniqueness (since $-S$ has these same initial conditions).

Now let's explore periodicity. Define $p(x) = S(x + \pi)$. Then:

$$p(x) = S(x + \pi/2 + \pi/2) = C(x + \pi/2) = -S(x)$$

So $S(x + \pi) = -S(x)$. Applying this again:

$$S(x + 2\pi) = S((x + \pi) + \pi) = -S(x + \pi) = -(-S(x)) = S(x)$$

Similarly, $C(x + 2\pi) = C(x)$.

Both functions are periodic with period $2\pi$, derived entirely from the ODE.

### 3.6 Trigonometric Identities

We will find the same identities for $S$, $C$, and $sin$, $cos$, then we can say they are “same”. Let's derive $S(x + y)$.

Fix $y$ and consider $$g(x) = S(x + y)$$

Then $g''(x) + g(x) = 0$, with $g(0) = S(y)$, $ g'(0) = S'(y) = C(y)$

Since the general solution to $f'' + f = 0$ is:

$$f(x) = A S(x) + B C(x)$$

we need to find constants $A$ and $B$ such that: $$A S(0) + B C(0) = S(y) \implies B = S(y)$$ $$A S'(0) + B C'(0) = C(y) \implies A = C(y)$$

Therefore:  $$S(x + y) = C(y) S(x) + S(y) C(x)$$.  Or more conventionally:

$$\boxed{S(x + y) = S(x)C(y) + C(x)S(y)}$$

By similar reasoning:

$$\boxed{C(x + y) = C(x)C(y) - S(x)S(y)}$$

These are the basic angle addition formulas, from which we can construct anything we learnt before.

### 3.7 Taylor Series

Since $S'' = -S$ and $S(0) = 0, S'(0) = 1$, we can find all derivatives at 0.

The pattern: $S^{(2k)}(0) = 0$ and $S^{(2k+1)}(0) = (-1)^k$. By Taylor's theorem:

$$S(x) = \sum_{k=0}^{\infty} \frac{S^{(k)}(0)}{k!} x^k = \sum_{k=0}^{\infty} \frac{(-1)^k}{(2k+1)!} x^{2k+1}$$

$$\boxed{S(x) = x - \frac{x^3}{3!} + \frac{x^5}{5!} - \frac{x^7}{7!} + \cdots}$$

Similarly for $C$:

$$\boxed{C(x) = 1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \frac{x^6}{6!} + \cdots}$$

### 3.8 Euler's Formula: The Grand Unification

Let's consider  $$f(x) = \exp(ix)$$  where $i = \sqrt{-1}$. If we differentiate:

$$f'(x) = i \exp(ix)$$

$$f''(x) = i^2 \exp(ix) = -\exp(ix) = -f(x)$$

So $f'' + f = 0$! With initial conditions:

$$f(0) = \exp(0) = 1$$ $$f'(0) = i \exp(0) = i$$

Now, since $f$ satisfies $f'' + f = 0$, we can write:

$$f(x) = A S(x) + B C(x)$$

From $f(0) = 1$: $B = 1$. From $f'(0) = i$: $A = i$. Therefore:

$$\boxed{\exp(ix) = C(x) + i S(x)}$$

**This is Euler's formula!** The complex exponential equals cosine plus $i$ times sine.

If we use traditional notation $\sin(x) = S(x)$ and $\cos(x) = C(x)$:

$$e^{ix} = \cos(x) + i\sin(x)$$

When $x = \pi$ (where $S(\pi) = 0$ and $C(\pi) = -1$):

$e^{i\pi} + 1 = 0$—one of the most beautiful equations in mathematics, relating five fundamental constants and two fundamental notations.

### 3.9 Geometric Interpretation

The equation $S^2 + C^2 = 1$ means the point $(C(x), S(x))$ lies on the unit circle for every $x$. As $x$ varies from 0 to $2\pi$, the point traces out the entire circle.

In the complex plane, $\exp(ix) = C(x) + iS(x)$ has magnitude:

$$|\exp(ix)| = \sqrt{C(x)^2 + S(x)^2} = 1$$

So it also traces the unit circle. The parameter $x$ represents arc length (or angle in radians) traveled around the circle.

This connects our purely analytic ODE definition to the geometric unit circle definition: they're describing the same object from different perspectives.

### 3.10 Complex Definitions

From Euler's formula, we can also write:

$$\exp(ix) = C(x) + iS(x)$$,   $$\exp(-ix) = C(x) - iS(x)$$

Adding these: $$C(x) = \frac{\exp(ix) + \exp(-ix)}{2}$$

Subtracting: $$S(x) = \frac{\exp(ix) - \exp(-ix)}{2i}$$

Using standard notation:

$$\boxed{\cos(x) = \frac{e^{ix} + e^{-ix}}{2}, \quad \sin(x) = \frac{e^{ix} - e^{-ix}}{2i}}$$

------

## 4. Hyperbolic Functions via $f'' - f = 0$

### 4.1 The Defining ODE

Now consider the ODE:

$$f''(x) - f(x) = 0$$

Notice the sign change from $f'' + f = 0$. This small change produces dramatically different behavior. Instead of oscillations, we get exponential growth.

- $\text{Sh}(x):=$ solution with $\text{Sh}(0) = 0, \text{Sh}'(0) = 1$
- $\text{Ch}(x):=$ solution with $\text{Ch}(0) = 1, \text{Ch}'(0) = 0$

These are the hyperbolic sine and hyperbolic cosine.

### 4.2 Derivative Relations

From $f'' = f$, if we set $\text{Dh}(x) = \text{Sh}'(x)$:

Similar to 3.2, we will finally have:

$$\text{Sh}'(x) = \text{Ch}(x), \text{Ch}'(x) = \text{Sh}(x)$$

Note the sign difference from the trigonometric case. Both derivatives are positive.

### 4.3 The Conservation Identity

Define: $$H(x) = \text{Ch}(x)^2 - \text{Sh}(x)^2$$

Then: $$H'(x) = 2\text{Ch}(x)\text{Ch}'(x) - 2\text{Sh}(x)\text{Sh}'(x)$$

$$= 2\text{Ch}(x)\text{Sh}(x) - 2\text{Sh}(x)\text{Ch}(x) = 0$$

So $H$ is constant:

$$H(0) = \text{Ch}(0)^2 - \text{Sh}(0)^2 = 1 - 0 = 1$$

Therefore:

$$\boxed{\text{Ch}(x)^2 - \text{Sh}(x)^2 = 1}$$

This is the equation of a hyperbola (hence "hyperbolic" functions), just as $\cos^2 + \sin^2 = 1$ is the equation of a circle.

### 4.4 Addition Formulas

By the same technique as for trig functions, fixing $y$ and considering $g(x) = \text{Sh}(x+y)$, which satisfies $g'' - g = 0$ with $g(0) = \text{Sh}(y)$ and $g'(0) = \text{Ch}(y)$:

$$\boxed{\text{Sh}(x+y) = \text{Sh}(x)\text{Ch}(y) + \text{Ch}(x)\text{Sh}(y)}$$

$$\boxed{\text{Ch}(x+y) = \text{Ch}(x)\text{Ch}(y) + \text{Sh}(x)\text{Sh}(y)}$$

Note the plus sign in the second formula (unlike the minus for cos).

### 4.5 Taylor Series

From $\text{Sh}'' = \text{Sh}$ with $\text{Sh}(0) = 0, \text{Sh}'(0) = 1$

The pattern is $\text{Sh}^{(2k)}(0) = 0$ and $\text{Sh}^{(2k+1)}(0) = 1$ (all positive).

$$\boxed{\text{Sh}(x) = x + \frac{x^3}{3!} + \frac{x^5}{5!} + \frac{x^7}{7!} + \cdots}$$

$$\boxed{\text{Ch}(x) = 1 + \frac{x^2}{2!} + \frac{x^4}{4!} + \frac{x^6}{6!} + \cdots}$$

Compare to $S$ and $C$—the same series but with all positive signs.

### 4.6 Connection to Exponentials

The exponential function $\exp(x)$ satisfies:

$$\exp''(x) = \exp(x)$$

So $\exp'' - \exp = 0$. Also, $\exp(-x)$ satisfies the same ODE (check: $(\exp(-x))'' = \exp(-x)$).

These form two linearly independent solutions. We can write:

$$\exp(x) = A \text{Sh}(x) + B \text{Ch}(x)$$

From $\exp(0) = 1$: $B = 1$. From $\exp'(0) = 1$: $A = 1$.

So: $$\exp(x) = \text{Sh}(x) + \text{Ch}(x)$$

Similarly, $\exp(-x) = -\text{Sh}(x) + \text{Ch}(x)$.

Solving for Sh and Ch:

$$\boxed{\text{Sh}(x) = \frac{\exp(x) - \exp(-x)}{2} = \frac{e^x - e^{-x}}{2}}$$

$$\boxed{\text{Ch}(x) = \frac{\exp(x) + \exp(-x)}{2} = \frac{e^x + e^{-x}}{2}}$$

Using standard notation: $\sinh(x) = \text{Sh}(x)$ and $\cosh(x) = \text{Ch}(x)$.

### 4.7 Geometric Interpretation

The equation $\text{Ch}^2 - \text{Sh}^2 = 1$ describes a hyperbola:

$$x^2 - y^2 = 1$$

The point $(\text{Ch}(t), \text{Sh}(t))$ traces out the right branch of this hyperbola (since $\text{Ch}(t) > 0$ for all $t$). The parameter $t$ represents "hyperbolic angle" or "rapidity"—it's analogous to the circular angle but for hyperbolas.

### 4.8 Inverse Hyperbolic Functions

Since $\text{Sh}$ is strictly increasing, it has an inverse. We can express it as:

$$\text{arsinh}(x) = \ln(x + \sqrt{x^2 + 1})$$

**Derivation**: If $y = \text{Sh}(x) = \frac{e^x - e^{-x}}{2}$, solve for $x$:

$$e^{2x} - 2ye^x - 1 = 0$$

Using the quadratic formula with $u = e^x$:

$$u = \frac{2y \pm \sqrt{4y^2 + 4}}{2} = y \pm \sqrt{y^2 + 1}$$

Since $e^x > 0$, we take the positive root:

$$e^x = y + \sqrt{y^2 + 1}$$

$$x = \ln(y + \sqrt{y^2 + 1})$$

So $\text{arsinh}(y) = \ln(y + \sqrt{y^2 + 1})$.

### 4.9 Complex Connection

Using Euler's formula:

$$\sin(ix) = \frac{e^{i \cdot ix} - e^{-i \cdot ix}}{2i} = \frac{e^{-x} - e^{x}}{2i} = \frac{i(e^{x} - e^{-x})}{2i} = i\sinh(x)$$

So: $$\boxed{\sinh(ix) = i\sin(x), \, \cosh(ix) = \cos(x)}$$

This beautiful relationship shows that trigonometric and hyperbolic functions are intimately connected through complex numbers. They are very similar, just evaluated at different (real vs. imaginary) arguments.

------

## 5. Advanced ODEs 

This section is just for extended reading. If your interest supports you well throughout these ODEs, you are halfway to success in MATH2560J.

### 5.1 The Logistic Equation

The ODE $$f'(x) = f(x)(1 - f(x))$$ models population growth with carrying capacity. This is nonlinear (quadratic in $f$).

**Solution by separation of variables**:

$$\frac{df}{f(1-f)} = dx$$

Using partial fractions:

$$\int \left(\frac{1}{f} + \frac{1}{1-f}\right) df = \int dx$$

$$\ln\left|\frac{f}{1-f}\right| = x + C$$

$$\frac{f}{1-f} = Ae^x$$

where $A = \pm e^C$. Solving for $f$:

$$f = \frac{Ae^x}{1 + Ae^x} = \frac{1}{1 + Be^{-x}}$$

where $B = 1/A$. With initial condition $f(0) = 1/2$, we get $B = 1$:

$$\boxed{f(x) = \frac{1}{1 + e^{-x}}}$$

This is the sigmoid function, ubiquitous in machine learning and biology.

### 5.2 The Riccati Equation

The general Riccati equation:

$$f'(x) = P(x) + Q(x)f(x) + R(x)f(x)^2$$

is nonlinear but has special properties. Certain Riccati equations connect to trigonometric or hyperbolic functions.

**Example**: $\boxed{f' = 1 + f^2}$ has solution $\boxed{f(x) = \tan(x)}$.

**Verification**: If $f(x) = S(x)/C(x)$ (where $S, C$ satisfy $S'= C, C' = -S$):

$$f'(x) = \frac{S'C - SC'}{C^2} = \frac{C \cdot C - S \cdot (-S)}{C^2} = \frac{C^2 + S^2}{C^2} = \frac{1}{C^2} = 1 + \frac{S^2}{C^2} = 1 + f^2$$

### 5.3 Legendre Polynomials

The Legendre equation:

$$(1-x^2)f''(x) - 2xf'(x) + n(n+1)f(x) = 0$$

has polynomial solutions for non-negative integer $n$. These are the Legendre polynomials $P_n(x)$.

For example:

- $P_0(x) = 1$
- $P_1(x) = x$
- $P_2(x) = \frac{1}{2}(3x^2 - 1)$

They're orthogonal on $[-1,1]$:

$$\int_{-1}^1 P_m(x) P_n(x) \, dx = 0 \quad \text{if } m \neq n$$

### 5.4 Chebyshev Polynomials

The Chebyshev equation:

$$(1-x^2)f''(x) - xf'(x) + n^2 f(x) = 0$$

has solutions $T_n(x)$ that satisfy:

$$T_n(\cos\theta) = \cos(n\theta)$$

This connects back to our trigonometric functions. The Chebyshev polynomials are essentially trigonometric functions in disguise.

------

## 6. Conclusion: The Unity of Mathematics

We've seen how differential equations provide a unified framework for defining and understanding classical functions:

1. Exponentials arise from $f' = f$—proportional growth
2. Trigonometric functions from $f'' + f = 0$—oscillation
3. Hyperbolic functions from $f'' - f = 0$—hyperbolic geometry
4. Special functions from various advanced ODEs

The differential equations don't describe these functions—they **are** these functions. Everything else follows from the fundamental relationship between a function and its derivatives. This perspective reveals the **essential nature** of these functions, not as geometric constructions or algebraic formulas, but as objects characterized by how they change. This is deeply aligned with calculus itself, which is fundamentally about change.

Moreover, we've seen how apparently different definitions (unit circle vs. ODE for trig functions, geometric series vs. ODE for exponentials) define the **same mathematical objects**. This is a profound lesson: mathematics has many equivalent formulations, and each reveals different aspects of truth.