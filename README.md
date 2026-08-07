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
2. Paste the prompt from [`anki-flashcard/prompt-v4.txt`](anki-flashcard/prompt-v4.txt)
3. Import the output into Anki using `|` as field separator

**Generate revision notes:**
1. Upload your PDF to ChatGPT or Claude
2. Paste the prompt from [`revision-notes/prompt-v2.txt`](revision-notes/prompt-v2.txt)
3. Save the markdown output

## Contents

```
anki-flashcard/
├── prompt-v1.txt
├── prompt-v2.txt
├── prompt-v3.txt
└── prompt-v4.txt          ← Current version

revision-notes/
├── prompt-v1.txt
└── prompt-v2.txt          ← Current version

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
| Anki Flashcard | [v4](anki-flashcard/prompt-v4.txt) | Create Anki flashcard decks from PDFs |
| Revision Notes | [v2](revision-notes/prompt-v2.txt) | Generate study notes from PDFs |
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

Create Anki-compatible flashcard decks from PDF documents. Version 4 is the latest and recommended.

### Features

- Extracts key content including bolded/highlighted information
- One fact per card (atomic design)
- Outputs in `Question | Answer` format for direct Anki import
- Includes reverse cards for key definitions
- File access fallback using pdfplumber for troubleshooting

### Usage

1. Upload your PDF to the AI assistant
2. Use the prompt from [`anki-flashcard/prompt-v4.txt`](anki-flashcard/prompt-v4.txt):

```
Using this PDF as a reference, create a flashcards deck for Anki called [PDF Name].
Include all bolded/highlighted key content and Higher Tier content.
Ensure all necessary content of the topic is covered.
Guidelines:
- One fact per card (atomic)
- Use simple, concise language
- Include reverse cards for key definitions (for two-way recall)
- Exclude questions that require a diagram
Output as a text file, one flashcard per line: Question | Answer
```

3. Import the output text file into Anki using pipe (`|`) as the field separator

## Revision Notes Prompts

Generate concise study notes from PDF references. Version 2 is the latest.

### Features

- Comprehensive topic coverage
- Includes bolded/highlighted content
- Proofreads for accuracy
- Outputs as markdown

### Usage

1. Upload your PDF to the AI assistant
2. Use the prompt from [`revision-notes/prompt-v2.txt`](revision-notes/prompt-v2.txt):

```
Using this PDF as a reference, write a concise notes on the topic with the exact title "[Topic title]".
Include all bolded/highlighted key content and Higher Tier content.
Ensure all necessary knowledge of the topic is covered.
Proofread the information in the reference provided, and ensure all the information in the notes is correct.
Output as a markdown file.
```

## File Access Fallback

If normal PDF upload doesn't work, use the file access prompt included in v4/v2 files:

```
[File Pathname]
Use the Filesystem tools to access the file, then read the PDF skill and use pdfplumber to extract the PDF.
```

## Version History

### Anki Flashcard Prompts
- **v1**: Basic two-prompt structure
- **v2**: Added pipe vs comma separation options
- **v3**: Minor clarifications
- **v4**: XML tags, atomic guidelines, file access fallback

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

## License

This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). You are free to share and adapt the material with attribution.
