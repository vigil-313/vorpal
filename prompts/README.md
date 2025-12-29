# Anti-Sycophancy Prompt Library

Context injection documents for conditioning AI systems toward accuracy over comfort.

## Quick Selection Guide

| If the AI will be... | Use |
|---------------------|-----|
| Having open-ended conversations, giving advice, exploring ideas | `general-chat.md` |
| Executing tasks, using tools, completing requests | `task-tool.md` |
| Writing, reviewing, or debugging code | `code-technical.md` |
| Analyzing data, evaluating hypotheses, synthesizing research | `research-analysis.md` |
| Helping with creative projects, writing, brainstorming | `creative-writing.md` |
| Advising on decisions, evaluating options, planning | `decision-planning.md` |

## Document Structure

Each domain document contains:

1. **Scope** — When to use this prompt
2. **Sycophancy Profile** — How sycophancy manifests in this domain
3. **Principles** — Domain-specific anti-sycophancy rules
4. **Interaction Protocol** — Specific triggers and required responses
5. **Failure Modes** — How the prompt can fail
6. **Session Preamble** — Ready-to-use condensed injection text

## Usage

**See [`docs/usage-guide.md`](../docs/usage-guide.md) for detailed integration instructions, code examples, and troubleshooting.**

### Quick Start
1. Select prompt from table above
2. Copy the **Session Preamble** section from that file
3. Inject as system prompt in your AI application
4. Test with inputs that typically trigger sycophancy

### Full Document vs. Preamble
- **Full document:** Complete coverage, ~600-800 words. Use with large context windows.
- **Preamble only:** Core rules, ~100-200 words. Use for production or constrained contexts.

### Combining Prompts
For hybrid use cases, combine preambles ordered by primary function. Include `core-principles.md` as foundation.

## Files

```
prompts/
├── core-principles.md      # Shared foundation (include with any domain)
├── general-chat.md         # Advice, exploration, self-reflection contexts
├── task-tool.md            # Task execution, tool use, request completion
├── code-technical.md       # Code writing, review, debugging
├── research-analysis.md    # Data analysis, hypothesis evaluation
├── creative-writing.md     # Creative projects, writing assistance
└── decision-planning.md    # Decision-making, planning, option evaluation

docs/
├── usage-guide.md          # Integration instructions and code examples
├── failure-modes-catalog.md # Cross-domain failure mode reference
└── design-notes.md         # Rationale and design decisions
```

## The Core Problem

AI systems face social pressure to validate users. This manifests as:

- Praising mediocre work
- Agreeing with flawed approaches
- Hiding errors in optimistic summaries
- Expressing false confidence
- Treating articulation as accomplishment

These prompts counteract that pressure by making accuracy the primary objective.

## When NOT to Use

- Casual/entertainment contexts where stakes are low
- Situations where the user explicitly wants encouragement over accuracy
- Crisis support or emotional contexts (where validation may be appropriate)

These are tools for truth-seeking contexts, not universal defaults.
