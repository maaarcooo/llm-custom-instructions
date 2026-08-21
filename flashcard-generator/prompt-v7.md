# flashcard-prompt-v7

> Standalone fallback for `flashcard-generator` skill v3.8. Feature parity with the skill — use when the skill feature is unavailable. Keep this file in sync with SKILL.md when either is updated.

## Prompt

```
Using the attached file as a reference, create a flashcard deck named after the source file.

Process:
- Verify accuracy. Where the material names or clearly implies a qualification and exam board (for example OCR A Level Computer Science), treat that specification as the authority on content and terminology. If the source is wrong and you are confident of the correct version, put the corrected version on the cards and list the fix in your chat response. An error the material itself reveals counts as clear: a swapped table, a mislabelled diagram, a claim the rest of the material contradicts. If you are not confident of the correct version, leave that content out and say why. Never put a statement you believe to be wrong on a card. Keep the source's version only where it is a legitimate syllabus-level simplification, and flag rather than add content the specification does not require. All flags go in the chat response, never in the output file
- Cover all key content: definitions, laws, equations, units, standard values, conditions, named processes, and common explain/justify points

Card style — terse, exam-aligned, quick to self-grade:
- One idea per card, judged flexibly. Answers are one to two short sentences. A definition may bundle one directly associated detail (its formula, unit, or key property) when they are naturally recalled together. Never bundle a reasoning chain or a second independent concept
- Bundle or split, not both: a detail bundled into a definition answer must not also get its own card. No answer may contain the answer to another card
- No "because..." padding on recall answers. If reasoning matters, it gets its own card
- No yes/no or true/false questions — rephrase so the answer must be produced from memory
- Each question has exactly one correct answer
- For key terms (terms the exam asks candidates to define), add a reverse card as a separate line: [definition] — what term is this? | [term]
- Write all mathematical expressions using standard LaTeX notation: inline with $...$ and display with $$...$$. Use LaTeX for all symbols, fractions, subscripts, superscripts, and special characters in equations

Card types — pick the best fit per piece of knowledge:
- Definition: What is X? | [definition]. For key terms, add the reverse as a separate line
- Recall: single facts, values, units, equations
- Formula application: alongside a formula card, optionally one single-step application ($R = \frac{V}{I} = \frac{6}{2} = 3\;\Omega$). Never multi-step
- Cloze: The SI unit of energy is the [...] | joule (J). Use sparingly, one deletion per card, only where the context cues recall without giving the answer away
- Explain: only where the source itself explains the reasoning and it is a likely exam point. State the mechanism in at most two sentences. Do not convert recall content into explain cards
- Enumeration: one card per list item, not one card per list. A list answer may contain at most 3 items, and only if the source treats them as a single fact

After generating, check the deck for exactly two things:
1. Cards whose answers contradict each other as phrased — rephrase each question to name its context
2. Concepts the source explicitly contrasts — add one compare card stating the specific point of divergence. No other compare cards, and never two compare cards for the same distinction

Do not create: questions requiring a diagram to answer, multi-step calculations, yes/no questions, answers that merely restate the question (omit and flag instead), or cards for content the source does not adequately explain. Deck size is determined by content density — let the material decide.

Output a plain text file named after the source file (e.g. Physics_Chapter_5.pdf → Physics_Chapter_5.txt), one card per line:
Question | Answer

Never use the | character inside a question or answer (write "magnitude of v", not |v|). No preamble, headers, blank lines, or markdown in the file.

In your chat response, report every fix, omission, kept simplification and out-of-spec flag as a bullet list in the manner of release notes: one line per item, each starting with Fixed:, Skipped:, Kept: or Flagged:, the point stated directly, no paragraphs. Nothing if there is nothing to report.

Example cards:
What is the unit of electrical resistance? | Ohm (Ω)
Define specific heat capacity | The energy required to raise the temperature of 1 kg of a substance by 1 °C
The energy required to raise the temperature of 1 kg of a substance by 1 °C — what quantity is this? | Specific heat capacity
What is impulse? | The change in momentum of an object when a force acts on it, equal to force times time ($F t = \Delta p$)
```

## File access prompt

> Append if the normal file upload does not work.

```
[File Pathname]
Use the Filesystem tools to access the file, then read the PDF skill and use pdfplumber to extract the PDF.
```

## Notes

- Full instruction parity with skill v3.8, including the card-type taxonomy, LaTeX equation formatting, and the v3.8 accuracy pass (specification as authority, confident fix on the cards, doubtful content left out, never a wrong card, release-note flags in chat). The only intentional difference is the trimmed example set (four cards vs the skill's full block)
- Examples cover one recall, one definition + reverse pair (showing the reverse-line mechanic), and one bundled definition with LaTeX (showing the bundle pattern and equation formatting)
- The | exclusion and yes/no ban are the two rules that break imports or quality silently; do not trim them in future versions
