# Definition 1's channel asymmetry: is it structural, or a hidden normalization?

## 1. The question

Definition 1 in Agrawal, Gans & Goldfarb (2025) characterises a cognitive tool as doing two
things at once: raising the success probability $p(se;\theta)$ and lowering the implementation
cost $c(e;\theta)$, subject to the ratio $p'/c'$ falling strictly in $\theta$. On the page, the
two channels look symmetric — condition (i) treats $p$ rising and $c$ falling as parallel
requirements, and condition (ii) treats their ratio as the object that matters, not either piece
alone. But the paper's own worked example in Section 4 only ever moves $p$; it never varies $c$
with $\theta$. That raises a natural question: if you try to isolate either channel on its own,
does Definition 1 actually treat them symmetrically — or does one channel turn out to be a free
lunch and the other a dead end?

## 2. The precision-only channel

Take the paper's own Section 4 functional forms and hold cost entirely fixed:
$$
p(se;\theta) = \sqrt{se+\theta}, \qquad c(e;\theta) = c(e) = e
$$
Definition 1 checks cleanly: condition (i) holds since $p$ strictly rises in $\theta$ while $c$
is constant in $\theta$ (weak inequality with equality); condition (ii) holds since
$p'(se;\theta)/c'(e) = \dfrac{s}{2\sqrt{se+\theta}}$ is strictly decreasing in $\theta$. This is
exactly the paper's own Proposition 3 setup, so the first-order condition reproduces eqs.
(57)–(59):
$$
e^*(\theta) = \frac{\alpha^2\Delta^2 s}{4} - \frac{\theta}{s}, \qquad
M(e^*(\theta);\theta) = \frac{\alpha^2\Delta^2 s}{4} + \frac{\theta}{s}
$$
so the **precision-channel value gain** from $\theta=0$ to $\theta$ is exactly $\theta/s$ —
scaled inversely by skill $s$. Low-skill agents gain more from this channel than high-skill
agents; this is the inverse-skill-bias mechanism the paper leans on in Section 4.

## 3. The cost-only channel

### 3a. Impossible under the paper's implicit normalization

The natural mirror image holds $p(se;\theta)=p(se)$ fixed and lets $\theta$ act only through
$c(e;\theta)$. Every cost function the paper actually writes down satisfies
$c(0;\theta)=0$ for all $\theta$ — implementing zero effort costs nothing, regardless of the
tool. Under that normalization, condition (ii) with $p$ fixed requires
$\partial c'(e;\theta)/\partial\theta > 0$ for every $e>0$. By the fundamental theorem of
calculus:
$$
\frac{\partial c(e;\theta)}{\partial\theta} = \int_0^e \frac{\partial c'(x;\theta)}{\partial\theta}\,dx > 0 \quad \text{for every } e>0
$$
This means $c(e;\theta)$ is strictly *increasing* in $\theta$ for every $e>0$ — directly
violating condition (i), which requires cost to weakly fall as $\theta$ rises. The failure is
**immediate**, holding at every effort level simultaneously the moment $e>0$ — not a breakdown
that appears only past some threshold effort, and not a restriction to some sub-domain of $e$.
Under $c(0;\theta)=0$, no cost-only tool satisfies Definition 1 at all.

At first pass this looked like a structural fact about cost-only tools in general. It isn't —
it's an artifact of the specific normalization $c(0;\theta)=0$, imported silently from the
paper's own worked example.

### 3b. Possible once that normalization is relaxed

Allow $c(0;\theta)$ itself to vary with $\theta$ — a fixed overhead component, separate from the
marginal cost of effort, that can shrink as the tool improves. The following explicit
construction, with $p(se;\theta)=p(se)$ fixed throughout, satisfies Definition 1 on the entire
domain $e\in[0,\infty)$, $\theta\in[0,\infty)$:
$$
c(e;\theta) = e + \frac{e^2}{2} + 1 - e^{-e} + e^{-\theta-e}
$$

Verification, term by term:

- **Condition (i):** $\dfrac{\partial c}{\partial\theta} = -e^{-\theta-e} < 0$ for all
  $e\ge0,\theta\ge0$ — cost strictly falls in $\theta$ everywhere.
- **Condition (ii):** $c'(e;\theta) = 1+e+e^{-e}\left(1-e^{-\theta}\right)$, so
  $\dfrac{\partial c'}{\partial\theta} = e^{-\theta-e} > 0$ for all $e,\theta\ge0$ — marginal cost
  strictly rises in $\theta$ everywhere, so with $p$ fixed, $p'/c'$ strictly falls in $\theta$.
- **Convexity:** $c''(e;\theta) = 1-e^{-e}\left(1-e^{-\theta}\right)$, strictly positive for every
  finite $(e,\theta)$ since $e^{-e}\le1$ and $1-e^{-\theta}<1$.
- **Non-negativity:** $c(0;\theta)=e^{-\theta}>0$ for every finite $\theta$, shrinking toward
  (never reaching) zero as $\theta\to\infty$; cost is strictly larger for any $e>0$.

A numerical check at $e=1,\theta=1$ confirms all four: $c(1;0)=2.5$ vs. $c(1;1)=2.267456$
(cost fell), $c'(1;0)=2.0$ vs. $c'(1;1)=2.232544$ (marginal cost rose), $c''(1;1)=0.767456>0$
(convex), and $c(0;1)=0.367879>0$ (positive overhead). So a fully valid cost-only cognitive
tool exists, on the whole domain, with no restriction on effort levels needed — once the
zero-effort-cost normalization is relaxed.

## 4. What the finding actually is

The asymmetry between the two channels is **contingent on an unstated modeling choice**, not a
structural feature of Definition 1 or of cognitive tools generally. Definition 1's conditions
are genuinely symmetric in $p$ and $c$ in isolation — a valid tool can act through either channel
alone. What breaks the symmetry is the paper's implicit normalization $c(0;\theta)=0$, adopted
silently in every functional form the paper writes down, under which a cost-only tool becomes
strictly impossible. The paper never surfaces this because Section 4 only ever varies $p$ with
$\theta$; it never constructs, and so never has occasion to test, a cost-only counterpart. Once
that hidden normalization is relaxed — allowing a $\theta$-dependent fixed overhead separate
from marginal effort cost — the cost-only channel is fully consistent with Definition 1, and the
apparent asymmetry between the two channels disappears entirely.
