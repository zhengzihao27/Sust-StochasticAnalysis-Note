---
name: latex-section-polish
description: Polish LaTeX lecture-note section files by improving sentence quality, readability, and logical flow while preserving mathematical content and existing theorem-style environments. Use when Codex needs to refine a section such as `section1.tex` or `section2.tex`, especially for probability, analysis, or stochastic-process notes where definitions, examples, theorems, and proofs should read more smoothly without materially changing formulas, theorem statements, or proof strategy.
---

# LaTeX Section Polish

Polish the target section directly in the `.tex` file unless the user explicitly asks for a separate draft.

## Required Context

Before editing a section file, read these project files when they exist:

- `theorems.tex`: defines theorem-like environments such as `\defnn`, `\thmnn`, `\propp`, `\cornnp`, `\pf`, and related formatting/proof wrappers
- `commands.tex`: defines user macros such as `\diff`, `\abs`, `\norm`, `\xredstar`, and other notation used throughout the notes
- `main.tex`: shows package setup, global preamble choices, and how chapter/section files are included into the document

Use these files to avoid:

- breaking custom theorem environments
- rewriting notation in ways that conflict with project macros
- introducing formatting that does not match the main document setup

## Core Goal

Improve:

- sentence naturalness and precision
- transitions between paragraphs, definitions, examples, theorems, and remarks
- readability of proof narration
- lecture-note style coherence
- proof-step correctness at the level of local mathematical logic

Preserve:

- mathematical meaning
- theorem statements and formulas
- proof strategy and main derivations
- existing LaTeX environments such as `\defnn`, `\thmnn`, `\pf`, `\ex`, `\prop`, `\cornnp`

## Editing Rules

Apply these rules consistently:

1. Keep the original LaTeX structure unless a small structural adjustment is necessary for clarity.
2. Do not rewrite theorem, proposition, corollary, or lemma content aggressively.
3. Make only minimal mathematical edits when the original text is logically incomplete, grammatically misleading, or missing a necessary connective step.
4. Prefer local edits over expansion; do not turn concise notes into a textbook.
5. Keep terminology consistent throughout the section.
6. Maintain a clean lecture-note tone: concise, formal, and readable.
7. When editing proofs, verify that each displayed equality or implication is actually justified by the previous line.

## What to Improve

### Introductory and transition text

- Make the opening motivate the section naturally.
- Add short transition sentences when the text jumps too quickly from one concept to the next.
- Clarify why an example or theorem is introduced if that role is not obvious.

### Definitions

- Rewrite awkward definitions into standard mathematical English.
- Make quantifiers and conditions easier to parse.
- After a definition, add at most one short bridging sentence if the next item depends on it.

### Examples

- Make the purpose of the example explicit when helpful.
- Improve wording around what the example shows or why it matters.

### Proofs

Polish proofs by improving logical narration, not by changing the argument.

Prefer moves like:

- replace abrupt statements with clear connectors such as `therefore`, `on the other hand`, `hence`, `applying this pathwise`, `this contradicts`, `it follows that`
- make implicit logical jumps explicit when they are short and standard
- state clearly what has been shown at the end of the proof
- if a limit or implication uses a standard path property such as continuity or density, say so briefly

Also actively verify the proof steps themselves. In particular, check for:

- circular reasoning, where the line being proved is used as an intermediate equality
- unjustified equal signs when only an implication has been shown
- conditionings on the wrong sigma-algebra
- use of measurability that has not yet been established
- hidden convergence steps that require `a.s.`, `L^1`, uniform integrability, or right-continuity

If such issues appear, fix them with the smallest mathematically correct local change while preserving the original proof strategy whenever possible.

Do not:

- introduce new proof methods unless the original proof is genuinely broken
- expand routine arguments beyond what is needed
- alter the core derivation unless the original is logically broken

## Recommended Workflow

1. Read `theorems.tex`, `commands.tex`, and `main.tex` first to understand the theorem system, custom commands, and document-level structure.
2. Read the target section and identify awkward phrasing, weak transitions, and proofs with abrupt logical jumps.
3. Check nearby chapter context only if terminology or notation may depend on it.
4. Edit the target file directly.
5. Re-read the edited section to ensure the tone is uniform, theorem environments remain intact, and proof steps are logically valid.

## Output Standard

When responding to the user after editing:

- summarize the main improvements briefly
- mention whether theorem/proof content was only lightly touched or whether local proof-step corrections were needed
- reference the edited file path
