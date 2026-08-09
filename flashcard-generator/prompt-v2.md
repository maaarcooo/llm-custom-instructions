# flashcard-prompt-v2

## Prompt

```
Using this PDF as a reference, create flashcards for Anki deck called [PDF Name].
Make sure all bolded or highlighted key content and Higher Tier content are included.
Use simple language, keep each flashcard as concise as possible, try to simplify things as much as possible.
Format each flashcard as Q: [Question] then next line A: [Answer]
```

## Export prompt (pipe separator)

```
Convert the generated flashcards into a plain text Artifact, with each line representing one flashcard in the format: Question | Answer
```

## Export prompt (comma separator)

```
Convert the generated flashcards into a plain text document, with each line representing one flashcard in the format: Question, Answer
Ensure that commas are only used to separate the question from the answer.
```

## Notes

- Pipe separator is recommended — it does not cause errors on flashcard import
- If Artifacts are not available, replace "Artifact" with "document"
- Artifacts are only available in Claude
