# flashcard-prompt-v3

## Prompt

```
Using this PDF as a reference, create flashcards deck for Anki called [PDF Name].
Make sure all bolded or highlighted key content and Higher Tier content are included.
Use simple language, keep each flashcard as concise as possible, try to simplify things as much as possible.
Format each flashcard as Q: [Question] then next line A: [Answer]
```

## Export prompt (pipe separator)

```
Create a text file, then convert the generated flashcards into the file with each line representing one flashcard in the format: Question | Answer
```

## Export prompt (comma separator)

```
Create a text file, then convert the generated flashcards into the file with each line representing one flashcard in the format: Question, Answer
Ensure that commas are only used to separate the question from the answer.
```

## Notes

- Pipe separator is recommended — it does not cause errors on flashcard import
- Artifacts are only available in Claude
