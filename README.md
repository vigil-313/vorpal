# Vorpal

Context injection prompts for conditioning AI systems toward accuracy over comfort.

> *He took his vorpal sword in hand;*
> *Long time the manxome foe he sought—*
> *So rested he by the Tumtum tree*
> *And stood awhile in thought.*
>
> *And, as in uffish thought he stood,*
> *The Jabberwock, with eyes of flame,*
> *Came whiffling through the tulgey wood,*
> *And burbled as it came!*
>
> *One, two! One, two! And through and through*
> *The vorpal blade went snicker-snack!*
> *He left it dead, and with its head*
> *He went galumphing back.*
>
> — Lewis Carroll, *Jabberwocky* (1871)

---

## What This Is

A library of system prompts designed to counteract sycophancy in AI assistants. Each prompt targets a specific domain where AI systems tend to validate users rather than provide accurate feedback.

## Quick Start

1. Choose a prompt from `prompts/` based on your use case
2. Copy the **Session Preamble** section from that file
3. Inject as your system prompt
4. See [`docs/usage-guide.md`](docs/usage-guide.md) for integration examples

## Prompts

| Domain | File | Use When |
|--------|------|----------|
| General Chat | [`general-chat.md`](prompts/general-chat.md) | Advice, exploration, self-reflection |
| Task/Tool | [`task-tool.md`](prompts/task-tool.md) | Executing tasks, using tools |
| Code | [`code-technical.md`](prompts/code-technical.md) | Writing, reviewing, debugging code |
| Research | [`research-analysis.md`](prompts/research-analysis.md) | Analysis, hypothesis evaluation |
| Creative | [`creative-writing.md`](prompts/creative-writing.md) | Writing feedback, creative work |
| Decisions | [`decision-planning.md`](prompts/decision-planning.md) | Evaluating options, planning |

## The Problem

AI systems face social pressure to keep users comfortable. This produces:

- Praising mediocre work
- Agreeing with flawed approaches
- Hiding errors in optimistic summaries
- Expressing false confidence
- Treating articulation as accomplishment

These prompts counteract that pressure.

## Documentation

- [`prompts/README.md`](prompts/README.md) — Prompt selection guide
- [`prompts/core-principles.md`](prompts/core-principles.md) — Shared foundation for all domains
- [`docs/usage-guide.md`](docs/usage-guide.md) — Integration instructions and code examples
- [`docs/failure-modes-catalog.md`](docs/failure-modes-catalog.md) — How prompts can fail
- [`docs/design-notes.md`](docs/design-notes.md) — Rationale and design decisions

## Origin

Based on the [Anti-Affirmation Manifesto](anti_affirmation_manifesto.md), expanded into domain-specific prompts.

## Author

vigil-313

## License

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — You can use, modify, and distribute this work, but you must give appropriate credit and link back to this project.
