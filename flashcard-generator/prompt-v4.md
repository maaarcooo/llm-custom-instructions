# flashcard-prompt-v4

## Prompt

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

## File access prompt

> Append if the normal file upload does not work.

```
[File Pathname]
Use the Filesystem tools to access the file, then read the PDF skill and use pdfplumber to extract the PDF.
```

## Notes

- Pipe separator does not cause errors on flashcard import
- Each card should be self-contained
