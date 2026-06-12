# revision-notes-prompt-v3

> Standalone fallback for the `revision-notes-generator` skill (claude-skills v3.7). Use when the skills feature is unavailable. Paste the prompt below with the source file attached.

```
Create revision notes from the attached study materials. Title the notes after the topic in the source, and output a single .md file named after the source file (e.g. Physics_Chapter_5.pdf → Physics_Chapter_5.md). The notes must give complete understanding of the topic without the reader needing the source or any external material.

Process:
1. Read the attached source in full, including figures, diagrams, tables, and worked examples.
2. Map the source structure: list every subheading, method, equation, condition, and worked example. This map is your coverage checklist.
3. Write the notes following the rules below.
4. Run the verification pass before output.

Content rules:
- Coverage (the floor): Every subheading, definition, equation, named process, method, and stated condition in the source must appear in the notes, however compressed. Omitting a method step (e.g. "maximum height occurs when vertical velocity = 0") is a coverage failure even if the surrounding topic is included.
- Signal density (the style): Every sentence must define, explain, or connect a concept. No restating headings, no filler, no redundancy. Length is not capped: a long, dense source produces long, dense notes. Conciseness means zero noise, not brevity.
- Self-contained: The reader must never need to consult the source. Where the source relies on a diagram, translate its content into prose, a table, or a structured description. Never write "see source" or "see diagram on page X".
- Fidelity with flagged additions: Reproduce the source faithfully. Adding correct knowledge beyond the source is permitted when needed for complete understanding (e.g. the source omits a spec point, or two source statements would otherwise appear contradictory), but every addition must be marked inline as: *(Beyond source: [the added fact].)* Only mark content that genuinely does not appear anywhere in the source, including its tip boxes, examiner notes, and worked examples. Reconcile any addition with nearby source content so the notes never contradict themselves.
- Worked examples: Where a source worked example teaches a reusable method (conservation-law checks, SUVAT strategy, deducing quark composition, equilibrium proofs), compress it into a short inline example showing the method. Omit worked examples that only substitute numbers into an already-stated formula.
- Error flagging: If a source statement appears to conflict with standard A-Level treatment, keep the source version but append a flag immediately after it: > ⚠ Check: source states X; standard treatment is Y. Never silently "correct" the source.
- Tier labelling (GCSE sources only): If the source distinguishes Higher Tier content, label it (HT). A-Level sources have no tiers; skip this entirely.

Output format:
- Title as H1
- Keep the source's section numbering in headings (e.g. "4.1.3 Motion Along a Straight Line") for cross-referencing; exclude sub-clause spec codes (e.g. "1.1.3 a)") and source formatting artefacts (page references, margins, branding)
- Key terms in bold on first definition
- Equations in LaTeX ($...$ inline, $$...$$ display)
- Tables for comparative or tabular content
- End with a Key Equations Summary table; add a Key Constants table if the source provides constants

Verification (mandatory final pass) — check each item and fix any failure before output:
- Every item in the step-2 coverage map appears in the notes
- All bolded/highlighted source content included
- Each factual claim re-checked; conflicts flagged with ⚠, not silently changed
- Every beyond-source addition is marked and consistent with nearby content
- No internal contradictions between sections
- No "see source" references; all diagram content translated
- No filler sentences; no formatting artefacts from the source
```

# Optional: override the default title

```
Title: "[Exact title]"
```

# Add in file access prompt if normal file upload does not work

```
[File pathname]
Use the Filesystem tools to access the file, then read the pdf-reading skill and extract the PDF, preserving bold/highlight formatting and describing figures where possible.
```
