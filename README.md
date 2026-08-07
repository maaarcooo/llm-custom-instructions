# LLM custom instructions

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![GitHub last commit](https://img.shields.io/github/last-commit/maaarcooo/LLM-Custom-Instructions)](https://github.com/maaarcooo/LLM-Custom-Instructions)

A collection of customizable prompts and instructions for enhancing interactions with AI assistants (ChatGPT, Claude). Focused on educational use cases including flashcard creation and study note generation.

## Table of Contents

- [Quick Start](#quick-start)
- [Contents](#contents)
- [Custom Instructions](#custom-instructions)
- [Anki Flashcard Prompts](#anki-flashcard-prompts)
- [Revision Notes Prompts](#revision-notes-prompts)
- [File Access Fallback](#file-access-fallback)
- [Version History](#version-history)
- [License](#license)

## Quick Start

**Create Anki flashcards from a PDF:**
1. Upload your PDF to ChatGPT or Claude
2. Paste the prompt from [`anki-flashcard/prompt-v5.md`](anki-flashcard/prompt-v5.md)
3. Import the output into Anki using `|` as field separator

**Generate revision notes:**
1. Upload your PDF to ChatGPT or Claude
2. Paste the prompt from [`revision-notes/prompt-v3.md`](revision-notes/prompt-v3.md)
3. Save the markdown output

## Contents

```
anki-flashcard/
├── prompt-v1.txt / .md
├── prompt-v2.txt / .md
├── prompt-v3.txt / .md
├── prompt-v4.txt / .md
└── prompt-v5.md           ← Current version

revision-notes/
├── prompt-v1.txt
├── prompt-v2.txt
└── prompt-v3.md           ← Current version

custom-instructions/
├── instructions-v1.txt
├── instructions-v2.txt
├── instructions-v3.txt
├── instructions-v4.txt
├── instructions-v4lite.txt  ← Concise version of the v4 line
├── instructions-v5.txt
├── instructions-v5.1.txt
├── instructions-v5.2.txt
├── instructions-v5.2.1.txt
├── instructions-v5.3.txt
└── instructions-v5.4.txt    ← Current version
```

| Prompt | Current | Description |
|--------|---------|-------------|
| Anki Flashcard | [v5](anki-flashcard/prompt-v5.md) | Create Anki flashcard decks from PDFs |
| Revision Notes | [v3](revision-notes/prompt-v3.md) | Generate study notes from PDFs |
| Custom Instructions | [v5.4](custom-instructions/instructions-v5.4.txt) | Tone, formatting, and length guidelines for AI responses |
| Custom Instructions (Lite) | [v4lite](custom-instructions/instructions-v4lite.txt) | Concise version of the v4 instructions |

## Custom Instructions

The [`custom-instructions/instructions-v5.4.txt`](custom-instructions/instructions-v5.4.txt) file contains general guidelines for AI responses, organized into three sections:

- **Tone**: Efficient base style, answer first with no preamble or closing recap, open disagreement rather than softened agreement
- **Formatting**: Structure by default once a reply covers 3 or more distinct points, 3-sentence paragraph cap with the key finding bolded, terse bullets for lists and short paragraphs for explanations, literal language outside writing tasks, no emoji, em dashes, or semicolons
- **Length**: Lead with the answer, no unrequested tangents, completeness over elaboration with depth on request

The v5 line is a deliberate narrowing. Versions v1 to v4 also carried unit and date standards plus a factuality section. From v5 onwards the instructions cover response shape only, on the basis that the rest is either model default behavior or better handled per conversation.

The older [`instructions-v4lite.txt`](custom-instructions/instructions-v4lite.txt) remains available as a condensed form of the v4 instructions, retaining the priority framework and factuality guidance in a shorter format.

### Usage

Copy the contents into your AI assistant's custom instructions or system prompt settings.

## Anki Flashcard Prompts

Create Anki-compatible flashcard decks from PDF documents. Version 5 is the latest and recommended.

v5 is a standalone fallback for the `anki-flashcard-generator` skill, at full instruction parity with it. Use the skill where it is available and this prompt where it is not.

### Features

- Extracts key content including bolded/highlighted information
- One idea per card, judged flexibly, with explicit bundle-or-split rules
- Card-type taxonomy: definition, recall, formula application, cloze, explain, enumeration
- Reverse cards for key terms, generated as separate lines
- Accuracy pass that fixes clear source errors and flags likely simplifications in chat
- Outputs in `Question | Answer` format for direct Anki import
- File access fallback using pdfplumber for troubleshooting

### Usage

1. Upload your PDF to the AI assistant
2. Paste the prompt block from [`anki-flashcard/prompt-v5.md`](anki-flashcard/prompt-v5.md)
3. Import the output text file into Anki using pipe (`|`) as the field separator

The earlier [`prompt-v4.txt`](anki-flashcard/prompt-v4.txt) remains available as a much shorter prompt if v5 is more structure than you need.

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

If normal PDF upload doesn't work, append the file access prompt included at the end of the v5 and v3 files:

```
[File Pathname]
Use the Filesystem tools to access the file, then read the PDF skill and use pdfplumber to extract the PDF.
```

The revision notes variant differs slightly, asking the extraction to preserve bold and highlight formatting and describe figures. Use the version in the file you are working from.

## Version History

### Anki Flashcard Prompts
- **v1**: Basic two-prompt structure
- **v2**: Added pipe vs comma separation options
- **v3**: Minor clarifications
- **v4**: XML tags, atomic guidelines, file access fallback
- **v5**: Rewritten as a standalone fallback at parity with the `anki-flashcard-generator` skill. Added the card-type taxonomy, bundle-or-split rules, the yes/no ban, the `|` character exclusion, and a post-generation contradiction check

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

### Revision Notes Prompts
- **v1**: Multi-variant prompt structure
- **v2**: Simplified with XML tags and file access fallback
- **v3**: Rewritten as a standalone fallback for the `revision-notes-generator` skill. Added the coverage map and mandatory verification pass, signal density over brevity, marked beyond-source additions, error flagging, and LaTeX output with a Key Equations table

## License

This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). You are free to share and adapt the material with attribution.
