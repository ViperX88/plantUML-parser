Absolutely—here’s a compact “math tricks we’ve been using” cheat-sheet.

# 1) Plain algebra & exponents

* **Pull constants / regroup fractions:** (\dfrac{a\cdot b}{c}=\dfrac{a}{c}\cdot b).
* **Exponent split:** (x^{p-q}=x^p/x^q).
* **Change of base identity:** (a^{\log_b n}=n^{\log_b a}).
* **Log rules:** (\log(xy)=\log x+\log y), (\log(x/y)=\log x-\log y), (\log b^t=t).
* **Monotonicity of (\log):** if (x\le y) then (\log x\le \log y).

# 2) Floors/ceilings & constant squeezes

* (\big\lceil\frac n2\big\rceil \le \frac n2+1).
* **Choose a nicer constant** (\alpha<1) with ( \frac n2+1\le \alpha n) for large (n) (e.g., (\alpha=\frac{9}{16}) holds for (n\ge16)). Lets you replace (\log(\tfrac n2+1)) by (\log(\alpha n)=\log n+\text{const}).

# 3) Series you keep meeting

* **Geometric:** (\sum_{i=0}^{k} r^i=\dfrac{1-r^{k+1}}{1-r}).

  * If (r>1): (\Theta(r^k)) (last term dominates).
* **Arithmetic powers (Faulhaber):** (\sum_{i=1}^{\ell} i^k=\Theta(\ell^{k+1})).
* **Harmonic:** (H_n=\sum_{i=1}^{n}\frac1i=\Theta(\log n)).
* **“Shrinking linears”:** (\sum_{i=0}^{\lfloor\log_b n\rfloor} \frac{n}{b^i}=\Theta(n)).

# 4) Sum manipulations

* **Reindexing:** (\sum_{i=0}^{\ell-1}(\ell-i)^k=\sum_{j=1}^{\ell} j^k) (let (j=\ell-i)).
* **Pulling constants out:** (\sum c\cdot f(i)=c\sum f(i)).
* **Anonymous-function semantics:** In (\sum_{i=1}^{n}\Theta(i)), pick **one** (f) with (f(i)\in\Theta(i)) for all (i); then sum (f(i)). Don’t choose a different function at each (i).

# 5) Asymptotic algebra (classes)

* **Definitions:**
  (g\in O(f)) ⇔ (g\le c f) eventually;
  (g\in \Omega(f)) ⇔ (g\ge c f) eventually;
  (g\in \Theta(f)) ⇔ both;
  (g\in o(f)) ⇔ (g/f\to0);
  (g\in \omega(f)) ⇔ (g/f\to\infty).
* **Algebra:** (O(f)+O(g)=O(f+g)=O(\max{f,g})), (O(f)\cdot O(g)=O(fg)).
* **Base-of-log irrelevance:** (\log_a n=\Theta(\log_b n)).
* **Absorbing lower orders:** if (g\in o(f)), then (f+g\in \Theta(f)).

# 6) RAM model choices

* **Uniform (unit cost):** each word op = (O(1)) ⇒ loops count iterations.
* **Bit-cost (log model):** time ∝ operand bit-length.
  E.g., repeated squaring: bit-length after step (i) is (2^i+1) ⇒ total ( \sum(2^i+1)=\Theta(2^n)).

# 7) Recurrences toolbox

* **Unrolling to leaves:**
  (T(n)=aT(n/b)+f(n)\Rightarrow T(n)=a^{\log_b n}T(1)+\sum_{i=0}^{\log_b n-1} a^i f(n/b^i)).
* **Critical term:** (a^{\log_b n}=n^{\log_b a}) (leaf count).
* **Cancellation trick (Case 1):**
  (a^i (n/b^i)^{\log_b a-\varepsilon}=n^{\log_b a-\varepsilon},(b^\varepsilon)^i) ⇒ geometric series.
* **Case 2 flattening:**
  (a^i (n/b^i)^{\log_b a}) becomes (n^{\log_b a}) (constant per level) ⇒ multiply by (\log_b n).
* **Karatsuba idea:** reduce multiplications, add more additions ⇒ (T(n)=3T(n/2)+O(n)=\Theta(n^{\log_2 3})).

# 8) Induction proof “moves”

* Replace (O(n)) by (c n) for some constant (c).
* Target a clean shape (T(n)\le d,n\log n) and **massage terms** into (dn\log n + (\text{const})\cdot n).
* Use easy inequalities for large (n): (\log n\le n/4) (for (n\ge16)) to convert stray (\log n) terms into linear terms that can be absorbed by choosing (d) big enough.

# 9) Input length choices

* **Element model:** input size is (n) (each key fits in a word).
* **Bit model:** input size is (n\log N) bits (each value in ({1,\dots,N}) needs (\log N) bits).

---

If you want, I can turn this into a 1-page PDF crib sheet with a few worked micro-examples beside each rule.
