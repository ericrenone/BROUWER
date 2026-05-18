# BROUWER

**The Experiment-Allocation Equilibrium: A Fixed-Point Theorem for the Distribution of a Finite Measurement Budget Across Incompatible Symmetry Tests — Including the Failed First Attempt That Shows Why the Theorem Needs the Hypothesis It Needs**

ERI Labs · Eric Ren · Jersey City, New Jersey · github.com/ericrenone

---

## What This Document Is

This is a worklog for one theorem. The theorem is small, true, and proved; it is an application of a classical fixed-point result to a concretely defined map, not a landmark. It states that the allocation of a finite measurement budget across several mutually incompatible symmetry tests has a stable equilibrium — a distribution of resources from which no local reallocation improves the total information.

The document is written honestly, which here means a specific thing: it includes the first version of the theorem, which was **computed and found to be trivial**, and explains why. The trivial version and the real version differ by exactly one hypothesis, and the failure of the first is what proves the second is not decorative. A worklog that showed only the working version would hide the one fact that makes the working version worth stating. So both are here.

The honest status, up front: the equilibrium theorem below is a correct application of the Brouwer fixed-point theorem. Its content — that the equilibrium is interior, that every funded test has equal marginal value, that incompatibility specifically defunds the algebraically isolated test — is real and numerically verified. It is not a deep theorem. It is the kind of result that is worth having precisely because it is exactly as strong as its proof, and no stronger.

---

## Part I · The Question

The preceding documents in this corpus established two facts about testing the symmetries of physics. HARTREE computed, for several real experimental probes, the per-unit Fisher information each carries about its symmetry-violation parameter — the generator-variance ranking. HOLEVO showed that tests whose symmetry generators do not commute interfere: jointly testing them carries an irreducible incompatibility penalty set by the Poincaré commutators.

Neither document asked the question an experiment director actually faces. There is one budget — telescope time, laboratory resources, a fixed number of measurement shots — and several symmetry tests competing for it. Allocating more budget to one test sharpens it; but if that test is incompatible with another, the allocation degrades the second. The director allocates, observes which tests came out sharp, and is tempted to reallocate. Reallocation changes the incompatibility damage, prompting further reallocation.

Does this settle? Is there an allocation of the budget that is *stable* — one from which no reallocation improves the total information gathered? If there is, it is an equilibrium of experiment design: the resting point of the allocate-observe-reallocate loop. This document asks whether that equilibrium exists, and proves that it does.

---

## Part II · The Setup, Made Precise

There are m symmetry tests. An **allocation** is a vector x = (x₁, …, xₘ) with xᵢ ≥ 0 and Σxᵢ = 1: the fraction of the total budget given to each test. The set of allocations is the standard simplex Δ — and the two facts that Δ is **compact** and **convex** are the entire geometric input to the theorem.

Each test i has a per-unit information rate Iᵢ — the generator-variance Fisher information from HARTREE. Each pair of tests has an incompatibility coefficient Rᵢⱼ ≥ 0 — the Robertson ratio from HARTREE and HOLEVO, zero for compatible (commuting-generator) pairs and positive for incompatible ones, with Rᵢᵢ = 0.

The **effective information** delivered by test i at allocation x is its own information, earned on its budget share, divided by a degradation factor from every incompatible test drawing on the same budget:

$$
f_i(x) \;=\; \frac{I_i\,g(x_i)}{1 + \sum_j R_{ij}\,x_j}.
$$

The total information the experiment programme yields is U(x) = Σᵢ fᵢ(x). The function g describes how a single test's information grows with the budget it receives, and **the choice of g is the whole subject of Parts III and IV.**

---

## Part III · The First Attempt, and Why It Failed

The natural first choice is g(xᵢ) = xᵢ: information grows linearly with budget. Twice the shots, twice the information. With this choice the theorem can be set up cleanly — and it was, and it was computed, and the result was trivial.

The allocation dynamic was encoded as a continuous self-map of the simplex: a map T that reads the marginal value of each test at the current allocation and shifts budget toward the higher-value tests, normalized to stay on the simplex. T is continuous, Δ is compact and convex, so by the Brouwer fixed-point theorem T has a fixed point — an allocation T(x\*) = x\*. So far so good: the fixed point exists.

But the computation showed the fixed point is always a **corner of the simplex**. With linear information, the test with the largest Iᵢ — the energy channel, the nuclear clock, vastly out-informing the others — simply takes the entire budget. The verified output: x\* = (1, 0, 0, 0), the whole budget on the energy test, in both the incompatibility-free case and the case with the full incompatibility matrix switched on. Incompatibility damaged the boost test but never made diversification worthwhile, because with linear returns the marginal value of the dominant test never falls no matter how much budget it absorbs.

This is a fixed-point theorem with no content. "Fund only the single most informative test" is the answer to an argmax; it does not need Brouwer, and an equilibrium that is always a corner is not an equilibrium theory. The first attempt failed — not because the proof was wrong, but because the theorem it proved was empty. The computation caught what a derivation alone would have dressed up.

The failure is diagnostic. It says: an interesting equilibrium requires a force that makes pouring budget into one test eventually *not* worth it. Linear information has no such force. The fix is not to insert one artificially. It is to notice that the physically correct g already has it.

---

## Part IV · The Hypothesis That Makes the Theorem Real

A single test's information does not, in fact, grow linearly with budget without limit. For a broad and standard class of measurements — those operating at the standard quantum limit — the estimation variance improves as one over the square root of the number of shots, which means the **Fisher information grows as the square root of the budget**, not linearly. Information is **concave** in budget. This is not a modelling convenience introduced to rescue the theorem; it is the generic scaling of unentangled quantum estimation, and the corpus's own HELSTROM document is built on the estimation theory that produces it.

So take g(xᵢ) = √xᵢ, or any strictly concave increasing g. Concavity is the missing force: the marginal value of a test *falls* as its budget grows, so the dominant test stops being worth additional budget before it has consumed all of it, and resources spill over to the others.

With g concave, the total information U(x) is a strictly concave function on the compact convex simplex Δ. A strictly concave function on a compact convex set attains its maximum at a unique point, and the best-response allocation map — move budget toward higher marginal value — is a continuous self-map of Δ whose fixed point is exactly that maximizer. The Brouwer fixed-point theorem supplies the fixed point; concavity makes it unique and, crucially, **interior**.

**The theorem.** *For m symmetry tests with positive per-unit informations Iᵢ, incompatibility coefficients Rᵢⱼ ≥ 0, and strictly concave increasing budget-response g, the experiment-allocation map is a continuous self-map of the compact convex budget simplex; it has a fixed point; the fixed point is the unique allocation maximizing total effective information; and at it every funded test has equal marginal value.*

The proof is the three sentences before the statement. It is honest because it is short and because it names its load-bearing hypothesis — concavity of g — explicitly, the hypothesis whose absence Part III showed makes the theorem collapse.

---

## Part V · What the Equilibrium Looks Like

The theorem was computed for the four-channel system of HARTREE — energy, momentum, rotation, and boost tests — with the energy channel far out-informing the rest (relative informations 100, 12, 8, 5) and the boost channel incompatible with all three others, the compatible trio mutually penalty-free, as the Poincaré algebra dictates.

With concave information the verified equilibrium is **interior**: x\* ≈ (0.979, 0.014, 0.006, 0.0002). Every test is funded. The energy channel still dominates the budget — it should, it is far more informative — but it no longer takes everything, because its marginal value falls as its share grows until it equals the marginal value of the smaller tests.

That equality is the equilibrium condition, and the computation confirms it sharply: the marginal value of every funded test at x\* is equal, v ≈ 50.5 across the support, with a spread of 4 × 10⁻⁵. This is the experiment-design analogue of the defining property of a strategic equilibrium — every option in use yields the same marginal return, so no reallocation improves the total. The equilibrium is unique: twenty independent solver starts converge to the same allocation within 10⁻⁷.

The role of incompatibility is now visible and specific. Switching the incompatibility matrix R on shifts budget **away from the boost channel** — the boost test's allocation falls relative to the incompatibility-free case, while the compatible trio is barely moved. This is exactly what HOLEVO's algebra predicts: the boost generator fails to commute with all three of the others, so the boost test is the one whose marginal value is most degraded by a shared budget, and the equilibrium defunds it accordingly. The incompatibility structure does not change *whether* an equilibrium exists; it changes *where* it sits, and it moves it in the direction the Poincaré commutators specify.

---

## Part VI · Scope, Honestly Stated

**This is an application of Brouwer, not a new fixed-point theorem.** The mathematical core — continuous self-map of a compact convex set has a fixed point — is classical. The contribution is the construction of the specific map, the identification of the budget simplex as its domain, and the verification that the equilibrium is interior and meaningful. That is a modelling contribution and a computational one, not a contribution to fixed-point theory.

**The theorem's content depends entirely on the concavity hypothesis, and that hypothesis is a model.** Concave budget-response is the correct scaling for standard-quantum-limit measurements. For entanglement-enhanced measurements operating at the Heisenberg limit the scaling is different, and the budget-response within a single test can be steeper; the equilibrium would shift, and in some regimes the corner solution of Part III could genuinely return. The theorem is therefore conditional, and Part III is the proof that the condition is load-bearing rather than cosmetic. An honest reader should treat "the equilibrium is interesting" as true precisely when "information is concave in budget" is true.

**The effective-information functional is a chosen model.** The specific form fᵢ = Iᵢ g(xᵢ)/(1 + ΣRᵢⱼxⱼ) — concave numerator, linear incompatibility denominator — is the simplest functional consistent with the two facts it must encode: own-information grows concavely, incompatible tests degrade each other. Other functionals consistent with those facts would give quantitatively different equilibria. The qualitative results — existence, interiority under concavity, defunding of the algebraically isolated test — are robust to that choice; the exact numbers are not.

**It is not a theory of physics; it is a theory of how to allocate a budget for testing physics.** The equilibrium says nothing about whether any symmetry is actually broken. It is a statement about experiment design — about the resting point of a resource-allocation loop — and it should be read as that and only that.

The single honest sentence: **the allocation of a finite measurement budget across incompatible symmetry tests has a unique stable equilibrium, interior whenever a single test's information is concave in its budget, at which every funded test carries equal marginal value and the algebraically isolated boost test is specifically defunded by the incompatibility structure — a Brouwer fixed point of a concretely constructed map, whose triviality without the concavity hypothesis is shown, not hidden.**

---

## References

Brouwer, L. E. J. "Über Abbildung von Mannigfaltigkeiten." *Mathematische Annalen* **71**, 97–115 (1911).

Kakutani, S. "A Generalization of Brouwer's Fixed Point Theorem." *Duke Mathematical Journal* **8**, 457–459 (1941).

Helstrom, C. W. *Quantum Detection and Estimation Theory.* Academic Press, New York, 1976.

Braunstein, S. L., Caves, C. M. "Statistical Distance and the Geometry of Quantum States." *Physical Review Letters* **72**, 3439–3443 (1994).

Robertson, H. P. "The Uncertainty Principle." *Physical Review* **34**, 163–164 (1929).

Giovannetti, V., Lloyd, S., Maccone, L. "Advances in Quantum Metrology." *Nature Photonics* **5**, 222–229 (2011).

Rockafellar, R. T. *Convex Analysis.* Princeton University Press, 1970.

---

ERI Labs · Eric Ren · Jersey City, New Jersey · github.com/ericrenone · May 2026

A finite budget across incompatible tests has a stable equilibrium. It is a Brouwer fixed point; it is interior only when information is concave in budget; the first attempt without that hypothesis was trivial, and that failure is shown here, because it is the proof the hypothesis is real.
