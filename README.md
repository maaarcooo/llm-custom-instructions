# LLM custom instructions

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![GitHub last commit](https://img.shields.io/github/last-commit/maaarcooo/LLM-Custom-Instructions)](https://github.com/maaarcooo/LLM-Custom-Instructions)

A collection of customizable prompts and instructions for enhancing interactions with AI assistants (ChatGPT, Claude). Focused on educational use cases including flashcard creation and study note generation.

## Table of Contents

- [Quick Start](#quick-start)
- [Contents](#contents)
- [Custom Instructions](#custom-instructions)
- [Flashcard Generator Prompts](#flashcard-generator-prompts)
- [Revision Notes Prompts](#revision-notes-prompts)
- [File Access Fallback](#file-access-fallback)
- [Version History](#version-history)
- [License](#license)

## Quick Start

**Create flashcards from a PDF:**
1. Upload your PDF to ChatGPT or Claude
2. Paste the prompt from [`flashcard-generator/prompt-v7.md`](flashcard-generator/prompt-v7.md)
3. Import the output into your flashcard app using `|` as field separator

**Generate revision notes:**
1. Upload your PDF to ChatGPT or Claude
2. Paste the prompt from [`revision-notes/prompt-v3.md`](revision-notes/prompt-v3.md)
3. Save the markdown output

## Contents

```
flashcard-generator/
├── prompt-v1.md
├── prompt-v2.md
├── prompt-v3.md
├── prompt-v4.md
├── prompt-v5.md
├── prompt-v6.md
└── prompt-v7.md           ← Current version

revision-notes/
├── prompt-v1.md
├── prompt-v2.md
└── prompt-v3.md           ← Current version

custom-instructions/
├── instructions-v1.md
├── instructions-v2.md
├── instructions-v3.md
├── instructions-v4.md
├── instructions-v4lite.md   ← Concise version of the v4 line
├── instructions-v5.md
├── instructions-v5.1.md
├── instructions-v5.2.md
├── instructions-v5.2.1.md
├── instructions-v5.3.md
├── instructions-v5.4.md
├── instructions-v5.5.md
├── instructions-v5.5.1.md  ← Current shared version
└── chatgpt-character-addon-v5.5.md
                              ← Optional ChatGPT character layer
```

| Prompt | Current | Description |
|--------|---------|-------------|
| Flashcard Generator | [v6](flashcard-generator/prompt-v6.md) | Create flashcard decks from PDFs |
| Revision Notes | [v3](revision-notes/prompt-v3.md) | Generate study notes from PDFs |
| Custom Instructions | [v5.5.1](custom-instructions/instructions-v5.5.1.md) | Shared presentation, formatting, length, and epistemic-discipline guidelines |
| ChatGPT Character Add-on | [v5.5](custom-instructions/chatgpt-character-addon-v5.5.md) | Optional character layer for a more curious, warm, independent ChatGPT |
| Custom Instructions (Lite) | [v4lite](custom-instructions/instructions-v4lite.md) | Concise version of the v4 instructions |

## Custom Instructions

The [`custom-instructions/instructions-v5.5.1.md`](custom-instructions/instructions-v5.5.1.md) file contains shared guidelines for AI responses, organized into four sections:

- **Tone**: Efficient presentation style, answer first with no preamble or closing recap, open disagreement rather than softened agreement
- **Formatting**: Structure by default once a reply covers 3 or more distinct points, 3-sentence paragraph cap with the key finding bolded, terse bullets for lists and short paragraphs for explanations, literal language outside writing tasks, no emoji, em dashes, or semicolons
- **Length**: Stay focused while allowing relevant implications or tensions, completeness over elaboration with depth on request
- **Epistemic discipline**: Accuracy over complete-sounding invention, clear separation of fact from inference, calibrated uncertainty, verification when appropriate, and direct correction of unsupported premises

For ChatGPT, [`custom-instructions/chatgpt-character-addon-v5.5.md`](custom-instructions/chatgpt-character-addon-v5.5.md) adds a separate character layer: intellectual curiosity, warmth without sycophancy, independent judgment, calibrated confidence, occasional understated wit, and a conversational mode that does not automatically turn every exchange into coaching or an action plan. Keeping it separate preserves one shared set of presentation preferences while allowing platform-specific character tuning.

The v5 line is a deliberate narrowing. Versions v1 to v4 also carried unit and date standards plus broader factuality guidance. Versions v5.1 through v5.5 reduced the shared instructions to response shape, leaving other behavior to model defaults, per-conversation guidance, or a platform-specific layer such as the ChatGPT add-on. Version 5.5.1 restores only the epistemic rules needed to prevent confident gap-filling and unsupported claims.

The older [`instructions-v4lite.md`](custom-instructions/instructions-v4lite.md) remains available as a condensed form of the v4 instructions, retaining the priority framework and factuality guidance in a shorter format.

### Usage

Copy [`instructions-v5.5.1.md`](custom-instructions/instructions-v5.5.1.md) into your AI assistant's custom instructions or system prompt settings. For ChatGPT, append the contents of [`chatgpt-character-addon-v5.5.md`](custom-instructions/chatgpt-character-addon-v5.5.md) in the same instruction field; the add-on is designed to complement rather than replace the shared file.

## Flashcard Generator Prompts

Create flashcard decks from PDF documents. Version 7 is the latest and recommended.

v7 is a standalone fallback for the `flashcard-generator` skill, at full instruction parity with it. Use the skill where it is available and this prompt where it is not.

### Features

- Extracts key content including bolded/highlighted information
- One idea per card, judged flexibly, with explicit bundle-or-split rules
- Card-type taxonomy: definition, recall, formula application, cloze, explain, enumeration
- Reverse cards for key terms, generated as separate lines
- Accuracy pass with the named exam board's specification as authority: confident fixes go on the cards and are listed in chat, doubtful content is left out with the reason given, simplifications are kept, out-of-spec content is flagged rather than added, and no card ever carries a statement the model believes wrong
- Chat flags as a release-note bullet list (`Fixed:` / `Skipped:` / `Kept:` / `Flagged:`)
- LaTeX equation formatting (KaTeX-compatible `$...$` / `$$...$$`)
- Outputs in `Question | Answer` format for direct import
- File access fallback using pdfplumber for troubleshooting

### Usage

1. Upload your PDF to the AI assistant
2. Paste the prompt block from [`flashcard-generator/prompt-v7.md`](flashcard-generator/prompt-v7.md)
3. Import the output text file into your flashcard app using pipe (`|`) as the field separator

The earlier [`prompt-v4.md`](flashcard-generator/prompt-v4.md) remains available as a much shorter prompt if v7 is more structure than you need.

## Revision Notes Prompts

Generate dense, self-contained study notes from PDF references. Version 3 is the latest.

v3 is a standalone fallback for the `revision-notes-generator` skill. Use the skill where it is available and this prompt where it is not.

### Features

- Coverage checklist built from the source structure, then verified in a mandatory final pass
- Signal density over brevity: length scales with the source, but every sentence must do work
- Self-contained output, with diagram content translated into prose or tables
- Beyond-source additions permitted but marked inline
- Error flagging that preserves the source version rather than silently correcting it
- LaTeX equations, plus a Key Equations summary table
- Outputs as markdown

### Usage

1. Upload your PDF to the AI assistant
2. Paste the prompt block from [`revision-notes/prompt-v3.md`](revision-notes/prompt-v3.md)
3. Save the markdown output

The prompt titles the notes from the source automatically. An optional override block in the same file sets an exact title.

## File Access Fallback

If normal PDF upload doesn't work, append the file access prompt included at the end of the v7 and v3 files:

```
[File Pathname]
Use the Filesystem tools to access the file, then read the PDF skill and use pdfplumber to extract the PDF.
```

The revision notes variant differs slightly, asking the extraction to preserve bold and highlight formatting and describe figures. Use the version in the file you are working from.

## Version History

### Flashcard Generator Prompts
- **v1**: Basic two-prompt structure
- **v2**: Added pipe vs comma separation options
- **v3**: Minor clarifications
- **v4**: XML tags, atomic guidelines, file access fallback
- **v5**: Rewritten as a standalone fallback at parity with the `anki-flashcard-generator` skill. Added the card-type taxonomy, bundle-or-split rules, the yes/no ban, the `|` character exclusion, and a post-generation contradiction check
- **v6**: Renamed from anki-flashcard to flashcard-generator. Removed Anki-specific language. Added LaTeX equation formatting (KaTeX-compatible `$...$` / `$$...$$`). Parity with `flashcard-generator` skill v3.7
- **v7**: Accuracy pass reworked: the named qualification and exam board's specification is the authority; a confident correction goes on the cards and is listed in chat, a doubtful one means the content is left out with the reason given, and no card ever carries a statement the model believes wrong. Out-of-spec content is flagged rather than added. Chat flags are a release-note bullet list (`Fixed:` / `Skipped:` / `Kept:` / `Flagged:`). Parity with `flashcard-generator` skill v3.8

### Custom Instructions
- **v1**: Basic tone, formatting, and standards guidelines
- **v2**: Expanded guidance with detailed formatting rules and factuality section
- **v3**: Added priority framework (Accuracy > Conciseness > Formatting), refined ambiguity handling
- **v4**: Condensed and more direct language while retaining all core guidelines
- **v4lite**: Most concise version, all core principles in a shorter format
- **v5**: Dropped the priority framework, reworked formatting around matching format to content, split factuality into an honesty and judgement section
- **v5.1**: Narrowed scope to response shape only, removing the standards and honesty sections. Introduced the explicit 3-point threshold for structure and a dedicated Length section
- **v5.2**: Added rules for multi-issue reviews, a 3-sentence paragraph cap, and bolding the key finding per section. Length reframed as completeness over elaboration
- **v5.2.1**: Reworded the review opener to a natural sentence with no label prefix
- **v5.3**: Extended the structure threshold to sub-points and single-concept explanations, capped plain prose at roughly 2 paragraphs, added the literal language and metaphor limit
- **v5.4**: Added a Tone section setting an efficient base style, no preamble or closing recap, and plain disagreement
- **v5.5**: Reframed the shared file as a presentation layer and loosened the literal-language and scope rules enough to admit useful implications, alternative interpretations, and occasional expressive phrasing. Added an optional ChatGPT character layer for curiosity, warmth without sycophancy, independent judgment, calibrated confidence, and mode-matched conversation
- **v5.5.1**: Removed the duplicated answer-first instruction from the Length section and added focused epistemic-discipline rules against invention, unsupported certainty, unmarked inference, and silent acceptance of false premises

### Revision Notes Prompts
- **v1**: Multi-variant prompt structure
- **v2**: Simplified with XML tags and file access fallback
- **v3**: Rewritten as a standalone fallback for the `revision-notes-generator` skill. Added the coverage map and mandatory verification pass, signal density over brevity, marked beyond-source additions, error flagging, and LaTeX output with a Key Equations table

## License

This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). You are free to share and adapt the material with attribution.
