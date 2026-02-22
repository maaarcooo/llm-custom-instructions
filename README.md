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
├── instructions-v4.txt      ← Current version
└── instructions-v4lite.txt  ← Concise version
```

| Prompt | Current | Description |
|--------|---------|-------------|
| Anki Flashcard | [v4](anki-flashcard/prompt-v4.txt) | Create Anki flashcard decks from PDFs |
| Revision Notes | [v2](revision-notes/prompt-v2.txt) | Generate study notes from PDFs |
| Custom Instructions | [v4](custom-instructions/instructions-v4.txt) | General behavioral guidelines for AI responses |
| Custom Instructions (Lite) | [v4lite](custom-instructions/instructions-v4lite.txt) | Concise version of the custom instructions |

## Custom Instructions

The [`custom-instructions/instructions-v4.txt`](custom-instructions/instructions-v4.txt) file contains general guidelines for AI responses:

- **Priority**: Accuracy > Conciseness > Formatting
- **Tone/Language**: Professional, natural tone with clear and concise English
- **Formatting**: Structured responses (concise for short questions, headers for complex ones), bold for key points, no emojis
- **Standards**: Metric units, Celsius, DD-MM-YYYY dates, 24-hour time format
- **Factuality/Transparency**: Skeptical approach, challenges incorrect information, avoids sycophancy, states uncertainty clearly, A-level academic standard

A more concise version is available as [`instructions-v4lite.txt`](custom-instructions/instructions-v4lite.txt), retaining all core principles in a shorter format suitable for AI assistants with limited custom instruction space.

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

### Revision Notes Prompts
- **v1**: Multi-variant prompt structure
- **v2**: Simplified with XML tags and file access fallback

## License

This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). You are free to share and adapt the material with attribution.
