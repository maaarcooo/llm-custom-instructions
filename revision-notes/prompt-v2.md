# revision-notes-prompt-v2

## Prompt

```
Using this PDF as a reference, write a concise notes on the topic with the exact title "[Topic title]".
Include all bolded/highlighted key content and Higher Tier content.
Ensure all necessary knowledge of the topic is covered.
Proofread the information in the reference provided, and ensure all the information in the notes is correct.
Output as a markdown file.
```

## File access prompt

> Append if the normal file upload does not work.

```
[File Pathname]
Use the Filesystem tools to access the file, then read the PDF skill and use pdfplumber to extract the PDF.
```
