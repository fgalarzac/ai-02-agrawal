[README.md](https://github.com/user-attachments/files/31442667/README.md)
# Repository 2 — Agrawal, Gans & Goldfarb (2025), "The Economics of Bicycles for the Mind"

NBER Working Paper 34034, July 2025. **Unrefereed** — circulated for discussion, not peer-reviewed.
Not to be confused with an arXiv paper of a different title occasionally attributed to these
authors; this repository works from the NBER PDF directly.

## What question the paper answers

Why does the empirical record on cognitive technology and inequality look contradictory?
Computers raised productivity *and* inequality. AI often raises productivity while *reducing*
inequality within firms. The paper builds one model of an agent doing iterative task
improvement, and shows both patterns are special cases of the same mechanism operating on
different parts of human capability.

The single mechanism it formalises: a cognitive tool is a substitute for **implementation
skill** but a complement to **judgment** — and judgment itself splits into two skills that
behave differently. **Opportunity judgment** (spotting a chance to improve the task) is always
complemented by a better tool. **Payoff judgment** (correctly acting on a successful
implementation) is only complemented *conditionally* — only when the tool's direct gain in
success probability isn't swamped by the effort it lets the agent stop supplying.

## The agent's problem

In each period, conditional on having identified an opportunity to improve the task, the agent
chooses effort $e_t \ge 0$ to maximise the net benefit of implementation:

$$
\max_{e_t \ge 0} \; M(e_t;\theta) = p(s e_t;\theta)\,\alpha\,\Delta \;-\; c(e_t;\theta)
$$

- $s \in (0,1]$: implementation skill
- $\alpha \in [0,1]$: payoff judgment — probability the agent realises the improvement value $\Delta$ conditional on success
- $p(se_t;\theta) \in [0,1]$: probability implementation succeeds, increasing and weakly concave in effort
- $c(e_t;\theta)$: cost of effort, increasing and weakly convex
- $\theta \ge 0$: quality of the cognitive tool available to the agent

The first-order condition is $p'(se_t^*;\theta)\,s\alpha\Delta = c'(e_t^*;\theta)$. Aggregated
across periods with opportunity-arrival probabilities $\gamma(t)$ and discount factor $\delta$,
this yields the agent's continuation value $V_0(\theta)$.

## The main result, with all its conditions

**Definition 1 (cognitive tool).** A parameter $\theta$ is a cognitive tool if, for all effort
levels $e$ and all $\theta' > \theta$:

1. $p(se;\theta') \ge p(se;\theta)$ and $c(e;\theta') \le c(e;\theta)$ — the tool weakly raises
   success probability and weakly lowers cost at every effort level; and
2. $\dfrac{p'(se;\theta)}{c'(e;\theta)}$ is strictly decreasing in $\theta$ for all $e>0$ — the
   tool strictly lowers the marginal-benefit-to-marginal-cost ratio of effort.

Together with the standing regularity assumptions ($p$ increasing and weakly concave in
effort; $c$ increasing and weakly convex), this is exactly what is needed for the result below
— nothing more is assumed.

**Proposition 1.** Let $e_t^*(\theta)$ be the effort level maximising $M(e;\theta)$ in period
$t$, and let $V_0(\theta)$ be the agent's expected task quality from $t=0$ given the
opportunity sequence $\{\gamma(t)\}_{t=0}^{\infty}$. As the agent adopts a cognitive tool
($\theta$ rises from $0$ to $1$):

1. **Effort falls:** $e_t^*(1) < e_t^*(0)$ for every $t$.
2. **Effort is time-invariant:** $e_t^*(\theta) = e^*(\theta)$ for all $t$ (conditional on an
   opportunity, the per-period problem doesn't depend on $t$, $\gamma(t)$, or continuation
   values).
3. **Expected value rises:** $V_0(1) > V_0(0)$.

*Intuition in one sentence:* a better tool lowers the marginal payoff of human effort relative
to its cost, so the agent optimally works less per opportunity — but because the tool also
directly raises success probability and cuts cost, the net benefit of each opportunity still
goes up, and so does the value of the whole process.

One thing worth flagging for slide 2: the proof (Appendix A.1) does **not** establish that
success probability itself, $p(se^*(\theta);\theta)$, rises with $\theta$ — only that net
value $M(e^*(\theta);\theta)$ does. The paper shows this comparison is genuinely ambiguous in
general (eq. 29) and requires additional structure on $p$ and $c$ to sign. That ambiguity is
exactly the seed of the paper's later, more conditional results (Prop 2's part on payoff
judgment, and Prop 3's variance threshold) — which is why we treat Proposition 1 as the floor
result here and take those up separately in `extensions.md`.

`hand/`: [one line description of what the photo shows — to fill in once the derivation is done]

## Repository contents

| File | What it is |
|---|---|
| `README.md` | This page |
| `prompts.md` | Raw LLM prompts and answers used this week |
| `hand/` | Hand-derivation photo(s) |
| `presentation.tex` / `.pdf` | 5-minute Beamer deck |
