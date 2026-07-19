# Contributing to KinserPedia

This repo exists so future SE I / SE II students benefit from what you learned. A short, accurate document beats a long, stale one.

## Requirements for every submission

**1. Descriptive title.** Someone scanning the file list should know what's inside without opening it. Good: `Deploying an ASP.NET App to AWS with Docker.md`. Bad: `notes.md`, `Sprint stuff.docx`.

**2. Metadata header at the top of the document:**

```
Target Audience: (e.g., Product Owners)
Keywords: (e.g., Scrum, PO, Sprint, Grooming, Backlog, Prioritization)
Summary: (e.g., Techniques to prioritize product backlog items.)
Author: Your Name (SE I/II, Semester 'YY)
Last Verified: Month Year
```

The semester and date matter more than you think — cloud UIs, APIs, and course structure all drift, and readers need to know how old your instructions are.

**3. Put the file in the right folder.** See the categories in the [README](README.md). If nothing fits, propose a new folder in your PR description.

## Format guidelines

- **Prefer Markdown (`.md`).** It renders on GitHub, it's diffable, and future students can fix your doc with a small PR instead of re-uploading a whole file. PDFs are acceptable for slide decks or documents with lots of screenshots.
- **Avoid `.docx`.** GitHub can't preview it, so every reader is forced to download the file. Export to PDF or convert to Markdown before submitting.
- **Give every file an extension.** Extensionless files show up as raw blobs.
- **Verify before you publish.** If your document includes code, run it first. If it includes UI steps, walk through them once more before submitting. Don't paste unedited AI/chatbot output — if you used AI to help draft, that's fine, but you are the author and you're vouching for correctness.

## Hard rules

- **Never commit credentials.** No passwords, API keys, tokens, app passwords, or account logins — real or "temporary." Use placeholders like `YOUR_APP_PASSWORD`. Remember: once pushed, a secret lives in git history and every fork forever, even after you delete the file. If you accidentally push a secret, rotate it immediately and open an issue.
- **No personal info** about classmates without their consent (names on your own authored work are encouraged — that's your credit).
- **Respect course policy.** Guidance, tooling walkthroughs, and process writeups are welcome. Don't upload graded solutions to active assignments.

## How to submit

1. Fork the repo.
2. Add your document to the appropriate folder.
3. Add a row for it in the README index table (include audience and Last Verified date).
4. Open a pull request. In the description, say in one or two sentences what the doc covers and why it's useful.

## Other valuable contributions

- Updating a **Last Verified** date after confirming a guide still works.
- Marking or removing broken links.
- Fixing errors in existing docs (small PRs welcome).
- Replacing outdated semester-specific handouts with current versions.
