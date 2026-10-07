# Quant Math Course — working notes for Claude

A project-driven course taught inside one WLJS notebook, `claude-wolfram.wln`: from WL basics to the
math behind quant finance and data science. Gopi is the student; Claude writes and evaluates the
cells through the `wljs-notebook` MCP server.

Current position, open threads and kernel state are in @PROGRESS.md — read it first, and update it
at the end of every session.

## How to teach

- **Momentum over tooling.** Optimize core concepts learned per hour. If a cell has a cosmetic
  rendering or interactivity glitch, confirm the math is right kernel-side, say so in a line, and
  move on. No deep dives into WLJS internals unless the math is wrong or Gopi asks.
- After finishing a module, offer the next one rather than polishing the last.
- Each module follows the same shape: a short `.md` idea cell, a worked code cell, an interactive
  `Manipulate` where a picture helps, and a closing "Why quants care" section tied to finance.

## Numeric output

- Round to **2 decimals by default**; raw 16-digit output is unreadable. Use more digits only where
  they carry the point (e.g. 4 for convergence to `e`, or small variances).
- WLJS ignores `$Post`, `$Pre` and `$PrePrint` (cell evaluation bypasses the kernel main loop), so
  there is no global switch. Use the helper from the Module 0 setup cell: `expr // fmt`, or
  `fmt[expr, n]` / `fmt[#, n] &` for `n` decimals.
- `fmt` only touches `Real` and `Complex`; exact values (`Pi`, `1/3`, integers) pass through, which
  keeps the symbolic-vs-numeric distinction visible.
- Default every new numeric cell to `// fmt` without being asked.

## Notebook mechanics

- The MCP server has no "open" or "save" tool. Open the notebook with
  `wljs-notebook "<path>/claude-wolfram.wln"` (it opens in the running app). Cells added through MCP
  are **not written to disk until Gopi saves in the app** — ask for a save before committing.
- Cell type is set by the first line: `.md` for markdown, otherwise Wolfram Language.
- Avoid `Print` and `Abort` in cells. `D` is a built-in — don't use it as a variable name.
- In `Manipulate`, inline the matrix literals rather than referencing globals; that pattern has
  worked reliably here.
