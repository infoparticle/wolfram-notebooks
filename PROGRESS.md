# Progress — Quant Math Course

Course notebook: `claude-wolfram.wln` (WLJS Notebook, Wolfram Engine 14.3).
Update this file at the end of every session.

## Where we are

**Last session: 2026-10-07.** Finished Module 5. **Next: Module 6 — Probability Foundations.**

| # | Module | Status |
|---|--------|--------|
| 0 | WL Basics for Math | done |
| 1 | Precalculus Foundations | not in the notebook — skipped, reason not recorded |
| 2 | Differential Calculus | done (limits, derivative, differentials, optimization, bond duration/convexity) |
| 3 | Integral Calculus | done (FTC, Riemann sums, numerical integration, expectation as an integral) |
| 4 | Linear Algebra I | done (vectors, dot product, matrices as machines, systems, singular matrices, `w.Σ.w`) |
| 5 | Linear Algebra II | done (eigenvectors, diagonalization, spectral theorem, PCA, SVD, market factor) |
| 6 | Probability Foundations | **next** |
| 7 | Bayesian Probability | to do |
| 8 | Fourier Analysis | to do |
| 9 | Stochastic Processes & Quant Applications | to do |
| 10 | Capstone | to do |

## Open threads

- Module 5 ends with an exercise not yet discussed: in the last cell change `rho` to `0.2` and `0.9`,
  and watch PC1's variance share and the diversification floor `Sqrt[rho]`.
- Module 5's PCA cell simulates returns and uses variance/covariance/correlation before they are
  defined. Module 6 is meant to pay that debt (random variables, distributions, expectation,
  variance, why simulation works).
- The Module 5 `Manipulate` (spin the vector) and the PCA scatter were verified kernel-side only;
  the rendering has not been checked by eye.

## Notebook layout quirks

- Cell order is not strictly module order: the bond price/duration/convexity cells
  ("Seeing the bond's risk", Module 2 material) sit at the very end of the notebook, *after* Module 5.
  Add new modules after the last cell of the previous module, not at the bottom.
- An output-style comparison cell (raw / `pp` / `TableForm` / ...) sits in Module 0. No style was
  formally chosen; Modules 4 and 5 use a list of `"label" -> value` rules piped through `fmt`.

## Kernel state a new session needs

A freshly opened notebook has an empty kernel. Before adding to a module, re-evaluate:

- the Module 0 setup cell — defines `fmt` and `pp`
- whichever earlier cells define symbols the new work reuses

Symbols later modules lean on:

| Symbol | Defined in | What it is |
|--------|-----------|------------|
| `fmt`, `pp` | Module 0 setup cell | rounding / pretty-print helpers |
| `price` | Module 2, bond cell | 5-year 5% annual bond priced off yield `r` |
| `u`, `v` | Module 4 | `{3,4}`, `{1,2}` |
| `A` | Module 4 | `{{2,1},{1,3}}` |
| `Σ` (`\[CapitalSigma]`), `w` | Module 4 | 3-asset covariance matrix, weights `{0.5,0.3,0.2}` |
| `vals`, `vecs`, `P`, `dd` | Module 5 | eigen-decomposition of `A` |
| `lam`, `q` | Module 5 | eigen-decomposition of `Σ` |
| `rets`, `pcVar`, `pcDir`, `scores` | Module 5 | 500 simulated 2-asset returns and their PCA |
