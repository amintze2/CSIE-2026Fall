---
name: add-class-question
description: Log a new student question into the Class Questions tab of opportunity-bank-template.html, grouped by domain. Use when the user wants to add, file, or upload a class question (or several), or mentions logging a question someone asked in class/office hours.
---

# Add Class Question

Files one or more student questions into `opportunity-bank-template.html`'s
"Class Questions" tab, grouped under the domain they relate to.

## 1. Collect the fields

If the user hasn't already supplied these in their message, ask for:

- **Domain** — the domain/opportunity area the question relates to (e.g.
  "Defense and National Security"). If the question isn't tied to any
  specific domain, use "General Questions".
- **Person** — who asked the question.
- **Week** — the week number the question was asked.
- **Question(s)** — one or more questions from that person, in that domain,
  for that week. A single submission can carry multiple questions.

A user may paste several domain/person/question groups at once (e.g. two
domains in one message) — parse all of them before editing the file, and
only ask follow-up questions for whatever's still missing (a common gap:
a later domain block omits the person because it's the same asker as the
one before it — confirm rather than assume).

## 2. File it

Open `opportunity-bank-template.html` and find:

```html
<div id="questions" class="tab-content">
```

Each domain is a `.card` block with an `<h4>` naming the domain and a table
with columns **Question | Asked By | Week | Answer / Notes** (no Status
column — it was intentionally removed from this template, do not add one
back).

- **If a `.card` already exists** whose `<h4>` matches the domain
  (case-insensitive), append new `<tr>` rows to that card's `<tbody>`,
  right after its existing rows.
- **If no matching card exists**, create a new `.card` block in the same
  style as the others, placed just before the "General Questions"
  catch-all card at the bottom. Give it a `<tr>` header row matching the
  four columns above.
- Each row: `<td>Question text</td><td>Person</td><td>Week</td><td>--</td>`
  (the last column is for an answer/notes if one exists later; default to
  `--` when there isn't one yet).
- Lightly correct obvious typos in the question text, but don't rewrite or
  rephrase the substance of the question.
- Leave every other tab and section of the file untouched.

## 3. Confirm

After editing, summarize what was added (domain, person, week, and the
question(s)) so the user can catch anything mis-filed.
