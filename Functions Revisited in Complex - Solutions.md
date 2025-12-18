# Functions Revisited in Complex - Solutions

Yuebo Hu, TA of MATH1560J, GC, SJTU

liuyejiang576@sjtu.edu.cn

October, 2025

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



### Solutions

### Problem Set A: Polar Form and De Moivre

**A1.** Convert to polar form:

(a) $3 + 3i$  
**Solution:**  
$r = \sqrt{3^2 + 3^2} = \sqrt{18} = 3\sqrt{2}$  
$\theta = \arctan(3/3) = \pi/4$  
$\boxed{3\sqrt{2}(\cos\frac{\pi}{4} + i\sin\frac{\pi}{4})}$

(b) $-1 + \sqrt{3}i$  
**Solution:**  
$r = \sqrt{(-1)^2 + (\sqrt{3})^2} = 2$  
$\theta = \pi - \arctan(\sqrt{3}) = \pi - \pi/3 = 2\pi/3$  
$\boxed{2(\cos\frac{2\pi}{3} + i\sin\frac{2\pi}{3})}$

(c) $-4i$  
**Solution:**  
$r = 4$, $\theta = -\pi/2$  
$\boxed{4(\cos(-\frac{\pi}{2}) + i\sin(-\frac{\pi}{2}))}$

(d) $-2 - 2i$  
**Solution:**  
$r = \sqrt{(-2)^2 + (-2)^2} = 2\sqrt{2}$  
$\theta = \pi + \pi/4 = 5\pi/4$  
$\boxed{2\sqrt{2}(\cos\frac{5\pi}{4} + i\sin\frac{5\pi}{4})}$

---

**A2.** Convert to rectangular form:

(a) $2e^{i\pi/6}$  
**Solution:**  
$2(\cos\frac{\pi}{6} + i\sin\frac{\pi}{6}) = 2(\frac{\sqrt{3}}{2} + \frac{i}{2})$  
$\boxed{\sqrt{3} + i}$

(b) $5e^{3i\pi/4}$  
**Solution:**  
$5(\cos\frac{3\pi}{4} + i\sin\frac{3\pi}{4}) = 5(-\frac{\sqrt{2}}{2} + i\frac{\sqrt{2}}{2})$  
$\boxed{-\frac{5\sqrt{2}}{2} + \frac{5\sqrt{2}}{2}i}$

(c) $e^{-i\pi/3}$  
**Solution:**  
$\cos(-\frac{\pi}{3}) + i\sin(-\frac{\pi}{3}) = \frac{1}{2} - i\frac{\sqrt{3}}{2}$  
$\boxed{\frac{1}{2} - \frac{\sqrt{3}}{2}i}$

---

**A3.** Compute using De Moivre's theorem:

(a) $(1 + i\sqrt{3})^6$  
**Solution:**  
$1 + i\sqrt{3} = 2(\cos\frac{\pi}{3} + i\sin\frac{\pi}{3})$  
$(1 + i\sqrt{3})^6 = 2^6(\cos\frac{6\pi}{3} + i\sin\frac{6\pi}{3}) = 64(\cos 2\pi + i\sin 2\pi)$  
$\boxed{64}$

(b) $(\frac{1}{2} + \frac{\sqrt{3}}{2}i)^{12}$  
**Solution:**  
$\frac{1}{2} + \frac{\sqrt{3}}{2}i = \cos\frac{\pi}{3} + i\sin\frac{\pi}{3}$  
$(\frac{1}{2} + \frac{\sqrt{3}}{2}i)^{12} = \cos\frac{12\pi}{3} + i\sin\frac{12\pi}{3} = \cos 4\pi + i\sin 4\pi$  
$\boxed{1}$

(c) $(\cos\frac{\pi}{8} + i\sin\frac{\pi}{8})^{16}$  
**Solution:**  
$(\cos\frac{\pi}{8} + i\sin\frac{\pi}{8})^{16} = \cos\frac{16\pi}{8} + i\sin\frac{16\pi}{8} = \cos 2\pi + i\sin 2\pi$  
$\boxed{1}$

---

**A4.** Find all solutions:

(a) $z^4 = 16$  
**Solution:**  
$16 = 16(\cos 0 + i\sin 0)$  
$z_k = 16^{1/4}(\cos\frac{0 + 2\pi k}{4} + i\sin\frac{0 + 2\pi k}{4}) = 2(\cos\frac{\pi k}{2} + i\sin\frac{\pi k}{2})$  
$\boxed{2, 2i, -2, -2i}$

(b) $z^3 = -8$  
**Solution:**  
$-8 = 8(\cos\pi + i\sin\pi)$  
$z_k = 2(\cos\frac{\pi + 2\pi k}{3} + i\sin\frac{\pi + 2\pi k}{3})$  
$\boxed{1 + i\sqrt{3}, -2, 1 - i\sqrt{3}}$

(c) $z^6 = -1$  
**Solution:**  
$-1 = \cos\pi + i\sin\pi$  
$z_k = \cos\frac{\pi + 2\pi k}{6} + i\sin\frac{\pi + 2\pi k}{6}$  
$\boxed{\cos\frac{\pi}{6} + i\sin\frac{\pi}{6}, \cos\frac{\pi}{2} + i\sin\frac{\pi}{2}, \cos\frac{5\pi}{6} + i\sin\frac{5\pi}{6}}$

$\boxed{\cos\frac{7\pi}{6} + i\sin\frac{7\pi}{6}, \cos\frac{3\pi}{2} + i\sin\frac{3\pi}{2}, \cos\frac{11\pi}{6} + i\sin\frac{11\pi}{6}}$

---

**A5.** Use De Moivre to prove:

(a) $\cos(4\theta) = 8\cos^4\theta - 8\cos^2\theta + 1$  
**Solution:**  
$(\cos\theta + i\sin\theta)^4 = \cos 4\theta + i\sin 4\theta$  
Expand LHS: $\cos^4\theta + 4i\cos^3\theta\sin\theta - 6\cos^2\theta\sin^2\theta - 4i\cos\theta\sin^3\theta + \sin^4\theta$  
Real part: $\cos 4\theta = \cos^4\theta - 6\cos^2\theta\sin^2\theta + \sin^4\theta$  
Using $\sin^2\theta = 1 - \cos^2\theta$:  
$\cos 4\theta = \cos^4\theta - 6\cos^2\theta(1 - \cos^2\theta) + (1 - \cos^2\theta)^2$  
$= \cos^4\theta - 6\cos^2\theta + 6\cos^4\theta + 1 - 2\cos^2\theta + \cos^4\theta$  
$= 8\cos^4\theta - 8\cos^2\theta + 1$  
$\boxed{\text{Proved}}$

(b) $\sin(5\theta)$ in terms of $\sin\theta$  
**Solution:**  
$(\cos\theta + i\sin\theta)^5 = \cos 5\theta + i\sin 5\theta$  
Imaginary part: $\sin 5\theta = 5\cos^4\theta\sin\theta - 10\cos^2\theta\sin^3\theta + \sin^5\theta$  
Using $\cos^2\theta = 1 - \sin^2\theta$:  
$\sin 5\theta = 5(1 - \sin^2\theta)^2\sin\theta - 10(1 - \sin^2\theta)\sin^3\theta + \sin^5\theta$  
$= 5\sin\theta - 10\sin^3\theta + 5\sin^5\theta - 10\sin^3\theta + 10\sin^5\theta + \sin^5\theta$  
$= 5\sin\theta - 20\sin^3\theta + 16\sin^5\theta$  
$\boxed{\sin(5\theta) = 5\sin\theta - 20\sin^3\theta + 16\sin^5\theta}$

---

### Problem Set B: Complex Exponentials

**B1.** Compute exactly:

(a) $|e^{2+3i}|$  
**Solution:**  
$|e^{2+3i}| = |e^2||e^{3i}| = e^2 \cdot 1 = e^2$  
$\boxed{e^2}$

(b) $e^{i\pi/3} \cdot e^{i\pi/6}$  
**Solution:**  
$e^{i\pi/3} \cdot e^{i\pi/6} = e^{i(\pi/3 + \pi/6)} = e^{i\pi/2} = i$  
$\boxed{i}$

(c) $(e^{i\pi/4})^{8}$  
**Solution:**  
$(e^{i\pi/4})^{8} = e^{i2\pi} = 1$  
$\boxed{1}$

---

**B2.** Solve for all complex $z$:

(a) $e^z = 1$  
**Solution:**  
$e^z = 1 = e^{2\pi i k}$  
$z = 2\pi i k$ for $k \in \mathbb{Z}$  
$\boxed{z = 2\pi i k}$

(b) $e^z = -1$  
**Solution:**  
$e^z = -1 = e^{i\pi + 2\pi i k}$  
$z = i\pi(2k + 1)$  
$\boxed{z = i\pi(2k + 1)}$

(c) $e^z = i$  
**Solution:**  
$e^z = i = e^{i\pi/2 + 2\pi i k}$  
$z = i(\pi/2 + 2\pi k)$  
$\boxed{z = i(\pi/2 + 2\pi k)}$

(d) $e^z = 2i$  
**Solution:**  
$2i = 2e^{i\pi/2} = e^{\ln 2 + i\pi/2}$  
$z = \ln 2 + i(\pi/2 + 2\pi k)$  
$\boxed{z = \ln 2 + i(\pi/2 + 2\pi k)}$

---

**B3.** Prove that $|e^{iz}| = e^{-\text{Im}(z)}$ for all complex $z$.  
**Solution:**  
Let $z = x + iy$, then $iz = i(x + iy) = -y + ix$  
$e^{iz} = e^{-y + ix} = e^{-y}e^{ix}$  
$|e^{iz}| = |e^{-y}||e^{ix}| = e^{-y} \cdot 1 = e^{-y}$  
Since $\text{Im}(z) = y$, we have $|e^{iz}| = e^{-\text{Im}(z)}$  
$\boxed{\text{Proved}}$

---

**B4.** Show that $e^{z+2\pi i} = e^z$ for all $z$.  
**Solution:**  
$e^{z+2\pi i} = e^z \cdot e^{2\pi i} = e^z \cdot (\cos 2\pi + i\sin 2\pi) = e^z \cdot 1 = e^z$  
$\boxed{\text{Proved}}$

---

**B5.** Find all $z$ such that $e^z$ is:

(a) Real and positive  
**Solution:**  
$e^z = e^x e^{iy}$ is real and positive when $e^{iy} = 1$  
$y = 2\pi k$ for $k \in \mathbb{Z}$  
$\boxed{z = x + 2\pi i k}$

(b) Real and negative  
**Solution:**  
$e^z = e^x e^{iy}$ is real and negative when $e^{iy} = -1$  
$y = \pi(2k + 1)$  
$\boxed{z = x + i\pi(2k + 1)}$

(c) Purely imaginary  
**Solution:**  
$e^z = e^x e^{iy}$ is purely imaginary when $e^{iy} = \pm i$  
$y = \pi/2 + \pi k$  
$\boxed{z = x + i(\pi/2 + \pi k)}$

---

### Problem Set C: Trigonometric Functions

**C1.** Compute exactly (in $a + bi$ form):

(a) $\sin(i)$  
**Solution:**  
$\sin(i) = \frac{e^{i\cdot i} - e^{-i\cdot i}}{2i} = \frac{e^{-1} - e^{1}}{2i} = i\frac{e - e^{-1}}{2} = i\sinh 1$  
$\boxed{i\sinh 1}$

(b) $\cos(i)$  
**Solution:**  
$\cos(i) = \frac{e^{i\cdot i} + e^{-i\cdot i}}{2} = \frac{e^{-1} + e^{1}}{2} = \cosh 1$  
$\boxed{\cosh 1}$

(c) $\sin(1 + i)$  
**Solution:**  
$\sin(1 + i) = \sin 1\cosh 1 + i\cos 1\sinh 1$  
$\boxed{\sin 1\cosh 1 + i\cos 1\sinh 1}$

(d) $\cos(2i)$  
**Solution:**  
$\cos(2i) = \frac{e^{i\cdot 2i} + e^{-i\cdot 2i}}{2} = \frac{e^{-2} + e^{2}}{2} = \cosh 2$  
$\boxed{\cosh 2}$

---

**C2.** Solve for all complex $z$:

(a) $\sin z = 0$  
**Solution:**  
$\sin z = 0 \Rightarrow e^{iz} = e^{-iz} \Rightarrow e^{2iz} = 1$  
$2iz = 2\pi i k \Rightarrow z = \pi k$  
$\boxed{z = \pi k}$

(b) $\cos z = 0$  
**Solution:**  
$\cos z = 0 \Rightarrow e^{iz} = -e^{-iz} \Rightarrow e^{2iz} = -1 = e^{i\pi(2k+1)}$  
$2iz = i\pi(2k+1) \Rightarrow z = \frac{\pi}{2}(2k+1)$  
$\boxed{z = \frac{\pi}{2}(2k+1)}$

(c) $\sin z = 2$  
**Solution:**  
Let $w = e^{iz}$, then $\frac{w - w^{-1}}{2i} = 2 \Rightarrow w^2 - 4iw - 1 = 0$  
$w = \frac{4i \pm \sqrt{-16 + 4}}{2} = i(2 \pm \sqrt{3})$  
$e^{iz} = i(2 \pm \sqrt{3}) = (2 \pm \sqrt{3})e^{i\pi/2}$  
$iz = \ln(2 \pm \sqrt{3}) + i(\pi/2 + 2\pi k)$  
$z = -i\ln(2 \pm \sqrt{3}) + \pi/2 + 2\pi k$  
$\boxed{z = \pi/2 + 2\pi k - i\ln(2 \pm \sqrt{3})}$

(d) $\cos z = i$  
**Solution:**  
Let $w = e^{iz}$, then $\frac{w + w^{-1}}{2} = i \Rightarrow w^2 - 2iw + 1 = 0$  
$w = \frac{2i \pm \sqrt{-4 - 4}}{2} = i(1 \pm \sqrt{2})$  
$e^{iz} = i(1 \pm \sqrt{2}) = (1 \pm \sqrt{2})e^{i\pi/2}$  
$iz = \ln|1 \pm \sqrt{2}| + i(\pi/2 + 2\pi k)$  
$z = -i\ln|1 \pm \sqrt{2}| + \pi/2 + 2\pi k$  
$\boxed{z = \pi/2 + 2\pi k - i\ln|1 \pm \sqrt{2}|}$

---

**C3.** Prove the identities:

(a) $\sin(z + \pi) = -\sin z$  
**Solution:**  
$\sin(z + \pi) = \frac{e^{i(z+\pi)} - e^{-i(z+\pi)}}{2i} = \frac{-e^{iz} + e^{-iz}}{2i} = -\sin z$  
$\boxed{\text{Proved}}$

(b) $\cos(z + \pi) = -\cos z$  
**Solution:**  
$\cos(z + \pi) = \frac{e^{i(z+\pi)} + e^{-i(z+\pi)}}{2} = \frac{-e^{iz} - e^{-iz}}{2} = -\cos z$  
$\boxed{\text{Proved}}$

(c) $\sin(\pi/2 - z) = \cos z$  
**Solution:**  
$\sin(\pi/2 - z) = \frac{e^{i(\pi/2 - z)} - e^{-i(\pi/2 - z)}}{2i} = \frac{ie^{-iz} + ie^{iz}}{2i} = \frac{e^{iz} + e^{-iz}}{2} = \cos z$  
$\boxed{\text{Proved}}$

(d) $|\sin z|^2 + |\cos z|^2 = ?$ (Is it always 1?)  
**Solution:**  
$|\sin z|^2 = \sin^2 x + \sinh^2 y$, $|\cos z|^2 = \cos^2 x + \sinh^2 y$  
$|\sin z|^2 + |\cos z|^2 = \sin^2 x + \cos^2 x + 2\sinh^2 y = 1 + 2\sinh^2 y$  
Not always 1, only when $y = 0$  
$\boxed{1 + 2\sinh^2 y}$

---

**C4.** Find all $z$ such that $\sin z = \cos z$.  
**Solution:**  
$\sin z = \cos z \Rightarrow \tan z = 1$  
$z = \pi/4 + \pi k$  
$\boxed{z = \pi/4 + \pi k}$

---

### Problem Set D: Hyperbolic Functions

**D1.** Compute:

(a) $\sinh(i\pi/2)$  
**Solution:**  
$\sinh(i\pi/2) = \frac{e^{i\pi/2} - e^{-i\pi/2}}{2} = \frac{i - (-i)}{2} = i$  
$\boxed{i}$

(b) $\cosh(i\pi)$  
**Solution:**  
$\cosh(i\pi) = \frac{e^{i\pi} + e^{-i\pi}}{2} = \frac{-1 + (-1)}{2} = -1$  
$\boxed{-1}$

(c) $\sinh(\ln 2)$  
**Solution:**  
$\sinh(\ln 2) = \frac{e^{\ln 2} - e^{-\ln 2}}{2} = \frac{2 - 1/2}{2} = \frac{3}{4}$  
$\boxed{\frac{3}{4}}$

(d) $\cosh(\ln 3)$  
**Solution:**  
$\cosh(\ln 3) = \frac{e^{\ln 3} + e^{-\ln 3}}{2} = \frac{3 + 1/3}{2} = \frac{5}{3}$  
$\boxed{\frac{5}{3}}$

---

**D2.** Prove:

(a) $\sinh(2z) = 2\sinh z\cosh z$  
**Solution:**  
$2\sinh z\cosh z = 2\cdot\frac{e^z - e^{-z}}{2}\cdot\frac{e^z + e^{-z}}{2} = \frac{e^{2z} - e^{-2z}}{2} = \sinh(2z)$  
$\boxed{\text{Proved}}$

(b) $\cosh(2z) = \cosh^2 z + \sinh^2 z$  
**Solution:**  
$\cosh^2 z + \sinh^2 z = \frac{e^{2z} + 2 + e^{-2z}}{4} + \frac{e^{2z} - 2 + e^{-2z}}{4} = \frac{2e^{2z} + 2e^{-2z}}{4} = \frac{e^{2z} + e^{-2z}}{2} = \cosh(2z)$  
$\boxed{\text{Proved}}$

(c) $\cosh z + \sinh z = e^z$  
**Solution:**  
$\cosh z + \sinh z = \frac{e^z + e^{-z}}{2} + \frac{e^z - e^{-z}}{2} = e^z$  
$\boxed{\text{Proved}}$

(d) $\cosh z - \sinh z = e^{-z}$  
**Solution:**  
$\cosh z - \sinh z = \frac{e^z + e^{-z}}{2} - \frac{e^z - e^{-z}}{2} = e^{-z}$  
$\boxed{\text{Proved}}$

---

**D3.** Solve for all complex $z$:

(a) $\sinh z = 0$  
**Solution:**  
$\sinh z = 0 \Rightarrow e^z = e^{-z} \Rightarrow e^{2z} = 1$  
$2z = 2\pi i k \Rightarrow z = \pi i k$  
$\boxed{z = \pi i k}$

(b) $\cosh z = 2$  
**Solution:**  
$\cosh z = 2 \Rightarrow e^z + e^{-z} = 4$  
Let $w = e^z$, then $w + w^{-1} = 4 \Rightarrow w^2 - 4w + 1 = 0$  
$w = 2 \pm \sqrt{3}$  
$z = \ln(2 \pm \sqrt{3}) + 2\pi i k$  
$\boxed{z = \ln(2 \pm \sqrt{3}) + 2\pi i k}$

(c) $\sinh z = i$  
**Solution:**  
$\sinh z = i \Rightarrow e^z - e^{-z} = 2i$  
Let $w = e^z$, then $w - w^{-1} = 2i \Rightarrow w^2 - 2iw - 1 = 0$  
$w = i$  
$e^z = i = e^{i\pi/2} \Rightarrow z = i\pi/2 + 2\pi i k$  
$\boxed{z = i(\pi/2 + 2\pi k)}$

---

**D4.** Express in terms of trig functions:

(a) $\sinh(ix)$ where $x$ is real  
**Solution:**  
$\sinh(ix) = \frac{e^{ix} - e^{-ix}}{2} = i\sin x$  
$\boxed{i\sin x}$

(b) $\cosh(ix)$ where $x$ is real  
**Solution:**  
$\cosh(ix) = \frac{e^{ix} + e^{-ix}}{2} = \cos x$  
$\boxed{\cos x}$

---

## Problem Set E: Applications and Synthesis

### E1. Chebyshev Polynomials

**Definition:** $T_n(\cos\theta) = \cos(n\theta)$

**(a) Show that $T_n(x)$ is indeed a polynomial in $x$**

From De Moivre's theorem:
$$(\cos\theta + i\sin\theta)^n = \cos(n\theta) + i\sin(n\theta)$$

Using the binomial theorem:
$$(\cos\theta + i\sin\theta)^n = \sum_{k=0}^n \binom{n}{k} \cos^{n-k}\theta (i\sin\theta)^k$$

Taking the real part (only even $k$ terms contribute):
$$\cos(n\theta) = \sum_{j=0}^{\lfloor n/2 \rfloor} \binom{n}{2j} \cos^{n-2j}\theta (i\sin\theta)^{2j}$$

Since $(i\sin\theta)^{2j} = (-1)^j \sin^{2j}\theta$ and $\sin^{2j}\theta = (1-\cos^2\theta)^j$, we substitute:
$$\cos(n\theta) = \sum_{j=0}^{\lfloor n/2 \rfloor} \binom{n}{2j} (-1)^j \cos^{n-2j}\theta (1-\cos^2\theta)^j$$

Letting $x = \cos\theta$:
$$T_n(x) = \sum_{j=0}^{\lfloor n/2 \rfloor} \binom{n}{2j} (-1)^j x^{n-2j} (1-x^2)^j$$

This is clearly a polynomial in $x$ with leading term $x^n$.

**Key Insight:** The complex exponential approach allows us to systematically extract the polynomial structure hidden in the trigonometric definition.

$\boxed{\text{Proved}}$

---

**(b) Find explicit formulas for $T_2(x), T_3(x), T_4(x)$**

For $T_2(x)$:
$$\cos(2\theta) = 2\cos^2\theta - 1 \Rightarrow T_2(x) = 2x^2 - 1$$

For $T_3(x)$:
$$\cos(3\theta) = 4\cos^3\theta - 3\cos\theta \Rightarrow T_3(x) = 4x^3 - 3x$$

For $T_4(x)$:
$$\cos(4\theta) = 8\cos^4\theta - 8\cos^2\theta + 1 \Rightarrow T_4(x) = 8x^4 - 8x^2 + 1$$

**Verification:** These can also be derived from the general formula in part (a):
- $T_2(x)$: $j=0$ term gives $x^2$, $j=1$ term gives $-\binom{2}{2}x^0 = -1$
- $T_3(x)$: $j=0$ term gives $x^3$, $j=1$ term gives $-3x$
- $T_4(x)$: $j=0$ term gives $x^4$, $j=1$ term gives $-6x^2$, $j=2$ term gives $+1$

$\boxed{T_2(x) = 2x^2 - 1,\quad T_3(x) = 4x^3 - 3x,\quad T_4(x) = 8x^4 - 8x^2 + 1}$

---

**(c) Prove that $T_n(x)$ satisfies: $T_{n+1}(x) = 2xT_n(x) - T_{n-1}(x)$**

Using the trigonometric identity:
$$\cos((n+1)\theta) + \cos((n-1)\theta) = 2\cos(n\theta)\cos\theta$$

Substituting the Chebyshev definition:
$$T_{n+1}(\cos\theta) + T_{n-1}(\cos\theta) = 2T_n(\cos\theta)\cos\theta$$

Letting $x = \cos\theta$:
$$T_{n+1}(x) + T_{n-1}(x) = 2xT_n(x)$$

Rearranging:
$$T_{n+1}(x) = 2xT_n(x) - T_{n-1}(x)$$

**Alternative Complex Proof:**
Consider $e^{i(n+1)\theta} + e^{-i(n+1)\theta} = (e^{i\theta} + e^{-i\theta})(e^{in\theta} + e^{-in\theta}) - (e^{i(n-1)\theta} + e^{-i(n-1)\theta})$
This directly gives the recurrence when converted to cosine form.

**Significance:** This recurrence allows efficient computation of Chebyshev polynomials and reveals their orthogonal polynomial structure.

$\boxed{\text{Proved}}$

---

### E2. Lagrange's Trigonometric Identity

**Prove:** $\sum_{k=0}^{n}\cos(kx) = \frac{\sin((n+1)x/2)\cos(nx/2)}{\sin(x/2)}$

Consider the complex sum:
$$S = \sum_{k=0}^{n} e^{ikx} = \frac{1 - e^{i(n+1)x}}{1 - e^{ix}}$$

Multiply numerator and denominator by $e^{-ix/2}$:
$$S = \frac{e^{-ix/2} - e^{i(n+1/2)x}}{e^{-ix/2} - e^{ix/2}} = \frac{e^{inx/2}(e^{-i(n+1)x/2} - e^{i(n+1)x/2})}{e^{-ix/2} - e^{ix/2}}$$

Using $\sin\theta = \frac{e^{i\theta} - e^{-i\theta}}{2i}$:
$$S = e^{inx/2} \cdot \frac{-2i\sin((n+1)x/2)}{-2i\sin(x/2)} = e^{inx/2} \cdot \frac{\sin((n+1)x/2)}{\sin(x/2)}$$

Taking the real part:
$$\sum_{k=0}^{n}\cos(kx) = \text{Re}(S) = \cos(nx/2) \cdot \frac{\sin((n+1)x/2)}{\sin(x/2)}$$

**Application:** This identity has applications in signal processing and Fourier analysis.

**Special Cases:**
- When $x=0$, use L'Hôpital's rule to recover $\sum_{k=0}^{n} 1 = n+1$
- When $x=\pi$, we get alternating sum of cosines

$\boxed{\text{Proved}}$

---

### E3. Evaluate Integrals and Sums

**(a) $\int_0^{2\pi} e^{\cos\theta} \cos(\sin\theta) d\theta$**

Consider the complex function $e^{e^{i\theta}} = e^{\cos\theta + i\sin\theta} = e^{\cos\theta}[\cos(\sin\theta) + i\sin(\sin\theta)]$

The real part is exactly our integrand:
$$\text{Re}(e^{e^{i\theta}}) = e^{\cos\theta}\cos(\sin\theta)$$

Now expand in series:
$$e^{e^{i\theta}} = \sum_{n=0}^{\infty} \frac{e^{in\theta}}{n!}$$

The integral becomes:
$$\int_0^{2\pi} e^{\cos\theta}\cos(\sin\theta) d\theta = \text{Re}\left(\int_0^{2\pi} e^{e^{i\theta}} d\theta\right) = \text{Re}\left(\sum_{n=0}^{\infty} \frac{1}{n!} \int_0^{2\pi} e^{in\theta} d\theta\right)$$

But $\int_0^{2\pi} e^{in\theta} d\theta = 0$ for $n \neq 0$ and $= 2\pi$ for $n=0$

Therefore:
$$\int_0^{2\pi} e^{\cos\theta}\cos(\sin\theta) d\theta = 2\pi$$

$\boxed{2\pi}$

---

**(b) $\sum_{n=0}^{\infty} \frac{\cos(n\theta)}{2^n}$**

Consider the complex sum:
$$S = \sum_{n=0}^{\infty} \frac{e^{in\theta}}{2^n} = \sum_{n=0}^{\infty} \left(\frac{e^{i\theta}}{2}\right)^n$$

This is a geometric series with ratio $r = \frac{e^{i\theta}}{2}$, so:
$$S = \frac{1}{1 - \frac{e^{i\theta}}{2}} = \frac{2}{2 - e^{i\theta}}$$

Multiply numerator and denominator by the conjugate $2 - e^{-i\theta}$:
$$S = \frac{2(2 - e^{-i\theta})}{(2 - e^{i\theta})(2 - e^{-i\theta})} = \frac{4 - 2e^{-i\theta}}{4 - 2(e^{i\theta} + e^{-i\theta}) + 1}$$

Using $e^{i\theta} + e^{-i\theta} = 2\cos\theta$:
$$S = \frac{4 - 2e^{-i\theta}}{5 - 4\cos\theta}$$

Taking the real part:
$$\sum_{n=0}^{\infty} \frac{\cos(n\theta)}{2^n} = \text{Re}(S) = \frac{4 - 2\cos\theta}{5 - 4\cos\theta}$$

**Alternative Approach:** This can also be derived using the formula for sum of cosines in geometric progression.

$\boxed{\frac{4 - 2\cos\theta}{5 - 4\cos\theta}}$

---

**(c) $\sum_{n=1}^{\infty} \frac{\sin(nx)}{n}$ for $0 < x < 2\pi$**

Consider the complex sum:
$$S = \sum_{n=1}^{\infty} \frac{e^{inx}}{n} = -\ln(1 - e^{ix})$$

This comes from the Taylor series for $-\ln(1-z)$ with $z = e^{ix}$.

Now separate real and imaginary parts. Let $1 - e^{ix} = 1 - \cos x - i\sin x$.

In polar form:
$$|1 - e^{ix}| = \sqrt{(1-\cos x)^2 + \sin^2 x} = \sqrt{2 - 2\cos x} = 2|\sin(x/2)|$$

Argument:
$$\arg(1 - e^{ix}) = \arctan\left(\frac{-\sin x}{1 - \cos x}\right) = \arctan\left(\frac{-2\sin(x/2)\cos(x/2)}{2\sin^2(x/2)}\right) = -\frac{\pi - x}{2}$$

Therefore:
$$-\ln(1 - e^{ix}) = -\ln(2|\sin(x/2)|) + i\frac{\pi - x}{2}$$

The imaginary part gives our sum:
$$\sum_{n=1}^{\infty} \frac{\sin(nx)}{n} = \frac{\pi - x}{2}$$

**Convergence Note:** This formula is valid for $0 < x < 2\pi$. At $x=0$, the sum is 0.

**Historical Significance:** This is a classic Fourier series that converges to a sawtooth wave.

$\boxed{\frac{\pi - x}{2}}$

---

### E4. Lucas's Theorem on Cube Roots

**Show that for any integers $a, b, c$:**
$$(a + b\omega + c\omega^2)(a + b\omega^2 + c\omega) = a^2 + b^2 + c^2 - ab - bc - ca$$
where $\omega = e^{2\pi i/3}$

Recall that $\omega^3 = 1$ and $1 + \omega + \omega^2 = 0$.

Let $X = a + b\omega + c\omega^2$ and $Y = a + b\omega^2 + c\omega$.

Multiply directly:
$$XY = (a + b\omega + c\omega^2)(a + b\omega^2 + c\omega)$$

Expand term by term:
$$= a^2 + ab\omega^2 + ac\omega + ab\omega + b^2\omega^3 + bc\omega^2 + ac\omega^2 + bc\omega^4 + c^2\omega^3$$

Simplify using $\omega^3 = 1$ and $\omega^4 = \omega$:
$$= a^2 + ab(\omega^2 + \omega) + ac(\omega + \omega^2) + b^2 + bc(\omega^2 + \omega) + c^2$$

Group terms:
$$= a^2 + b^2 + c^2 + (ab + ac + bc)(\omega + \omega^2)$$

But $\omega + \omega^2 = -1$ (since $1 + \omega + \omega^2 = 0$), so:
$$XY = a^2 + b^2 + c^2 - (ab + ac + bc)$$

**Geometric Interpretation:** This represents the norm from the cubic field $\mathbb{Q}(\omega)$ to $\mathbb{Q}$.

**Application:** Used in solving cubic equations and in number theory.

$\boxed{\text{Proved}}$

---

### E5. Prove that $\prod_{k=1}^{n-1}\sin\frac{k\pi}{n} = \frac{n}{2^{n-1}}$

Consider the equation $z^n - 1 = 0$ with roots $z_k = e^{2\pi ik/n}$ for $k=0,1,\dots,n-1$.

Factor:
$$z^n - 1 = \prod_{k=0}^{n-1} (z - z_k)$$

Divide by $(z-1)$ (the $k=0$ root):
$$\frac{z^n - 1}{z - 1} = \prod_{k=1}^{n-1} (z - z_k) = z^{n-1} + z^{n-2} + \cdots + 1$$

Take the limit as $z \to 1$:
$$\lim_{z \to 1} \frac{z^n - 1}{z - 1} = n = \prod_{k=1}^{n-1} (1 - z_k)$$

Now take modulus:
$$n = \left|\prod_{k=1}^{n-1} (1 - e^{2\pi ik/n})\right| = \prod_{k=1}^{n-1} |1 - e^{2\pi ik/n}|$$

But $|1 - e^{2\pi ik/n}| = 2|\sin(\pi k/n)|$, so:
$$n = \prod_{k=1}^{n-1} 2\sin(\pi k/n) = 2^{n-1} \prod_{k=1}^{n-1} \sin(\pi k/n)$$

Therefore:
$$\prod_{k=1}^{n-1} \sin(\pi k/n) = \frac{n}{2^{n-1}}$$

$\boxed{\text{Proved}}$

---

### E6. Partial Fractions in the Complex Domain

**Show that:** $\frac{1}{1-z^n} = \frac{1}{n}\sum_{k=0}^{n-1}\frac{1}{1-\omega^k z}$ where $\omega = e^{2\pi i/n}$

We want to find constants $A_k$ such that:
$$\frac{1}{1-z^n} = \sum_{k=0}^{n-1} \frac{A_k}{1-\omega^k z}$$

Multiply both sides by $1-z^n$:
$$1 = \sum_{k=0}^{n-1} A_k \frac{1-z^n}{1-\omega^k z}$$

But $1-z^n = (1-\omega^k z)(1 + \omega^k z + \omega^{2k} z^2 + \cdots + \omega^{(n-1)k} z^{n-1})$

So:
$$1 = \sum_{k=0}^{n-1} A_k (1 + \omega^k z + \omega^{2k} z^2 + \cdots + \omega^{(n-1)k} z^{n-1})$$

This must hold for all $z$. Comparing coefficients:

For the constant term:
$$1 = \sum_{k=0}^{n-1} A_k$$

For $z^m$ terms ($m=1,\dots,n-1$):
$$0 = \sum_{k=0}^{n-1} A_k \omega^{mk}$$

This is a system of $n$ equations. The solution is $A_k = \frac{1}{n}$ for all $k$, because:
$$\sum_{k=0}^{n-1} \omega^{mk} = 0 \quad \text{for } m \not\equiv 0 \pmod{n}$$

Therefore:
$$\frac{1}{1-z^n} = \frac{1}{n}\sum_{k=0}^{n-1}\frac{1}{1-\omega^k z}$$

**Application:** Fundamental in signal processing, combinatorics, and the theory of finite fields.

$\boxed{\text{Proved}}$

---



## Epilogue

> "The essence of mathematics is not to make simple things complicated, but to make complicated things simple."
>
> — **Stan Gudder**




> The complex numbers are a natural extension of the real numbers, just as the real numbers are a natural extension of the rationals. Each extension resolves paradoxes and reveals deeper truths about the mathematical universe. In learning to see through complex eyes, we don't just solve harder problems—we see familiar problems in their true light. As you continue your mathematical journey, remember that the most profound insights often come from connecting different domains of knowledge and seeing the world through multiple perspectives—real and complex, algebraic and geometric, concrete and abstract. Keep exploring, keep questioning, and may your curiosity always lead you to beautiful mathematics.
>
> — **Yuebo Hu**



