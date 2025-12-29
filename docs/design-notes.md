# Design Notes

Rationale, tradeoffs, and design decisions for the Anti-Sycophancy Prompt Library.

---

## Core Design Philosophy

### Why Domain-Specific Prompts?

Sycophancy is not monolithic. It manifests differently across contexts:

| Context | Sycophancy Looks Like |
|---------|----------------------|
| General chat | Validating self-descriptions |
| Task execution | Declaring premature success |
| Code review | Praising working-but-bad code |
| Research | Confirming hypotheses |
| Creative work | Hollow enthusiasm |
| Decision-making | Supporting preferred options |

A single prompt cannot effectively address all these patterns. Domain-specific prompts allow:
- Targeted intervention on the specific sycophancy pattern
- Appropriate tone for the context
- Relevant interaction protocols
- Context-appropriate failure mode awareness

### Why Both Full and Preamble Versions?

**Full versions** provide:
- Rationale (helps the model understand *why*)
- Comprehensive failure mode coverage
- Detailed interaction protocols
- Useful for debugging and refinement

**Preambles** provide:
- Context window efficiency
- Easier integration
- Faster iteration
- Production deployment

Different use cases have different constraints.

---

## Key Design Decisions

### 1. Procedure Over Philosophy

Early drafts contained more philosophical framing. Testing revealed that models respond better to:
- Specific behavioral instructions
- Clear trigger-response mappings
- Concrete examples

Philosophy helps humans understand; procedure helps models behave. The documents retain enough philosophy to motivate the procedure, but lead with action.

### 2. Failure Modes Included

Each domain document includes its own failure modes section. This is intentional redundancy for:
- Context-relevant failure awareness
- Self-diagnostic capability
- Preventing over-correction

The cross-domain failure catalog (`docs/failure-modes-catalog.md`) provides comprehensive coverage for developers refining prompts.

### 3. No Universal Tone

The general-chat prompt has a more philosophical, austere tone. The task-tool prompt is more procedural. This is intentional:
- Tone should match context
- Severity appropriate to stakes
- Task contexts need efficiency over atmosphere

### 4. Guardrails Explicit

Each prompt includes guardrails against over-application:
- Not cruelty
- Not nihilism
- Proportionality to stakes
- Exit without ceremony

Anti-sycophancy can become its own performance. The guardrails help prevent that.

### 5. Session Preambles Are Self-Contained

Preambles don't reference the full document. They're designed to work independently:
- Different injection points in different systems
- Some systems can only use short system prompts
- Allows A/B testing between versions

---

## Tradeoffs and Limitations

### Length vs. Effectiveness

Longer prompts provide more coverage but:
- Consume context window
- May dilute key instructions
- Harder to maintain

Current calibration: Full documents ~600-800 words, Preambles ~100-200 words.

Testing needed to determine optimal length for specific models and use cases.

### Specificity vs. Generalizability

Highly specific protocols ("when user says X, respond with Y") are reliable but:
- Miss variations in user phrasing
- Can feel mechanical
- May not generalize to edge cases

Current approach: Provide specific protocols as examples, trust model generalization.

### Strictness vs. Usability

Very strict anti-sycophancy can:
- Frustrate users
- Make interactions unpleasant
- Reduce usage (users go elsewhere)

Current approach: Calibrate to stakes. Not everything needs maximum rigor. Low-stakes interactions allow more flexibility.

### Tone Bleed

Anti-sycophancy prompts can shift model behavior beyond the intended targets. Observed second-order effects:

- **Vocabulary shifts:** Models may adopt blunter language, including profanity, when the prompt's register permits directness
- **Threshold changes:** What feels "appropriate" to say moves — the model may be more willing to use harsh or informal language
- **Register absorption:** The tone of the prompt document itself (austere, philosophical, clinical) can infect the model's general output style

**Example:** During development of this library, a model was instructed to "start behaving immediately as the manifesto dictates." Later, when explaining why the name "vorpal" fit the project (referencing its Jabberwocky origin of cutting through nonsense), the model described the project's purpose as "cuts through bullshit." The profanity wasn't directed at the user or evaluating user input — it appeared in the model's own descriptive language about the project, matching the manifesto's unvarnished register.

**Why this happens:**
1. Prompts that emphasize "directness over comfort" lower the model's hedging instincts broadly
2. The prompt's own language serves as a style example
3. Permission to be critical in one dimension (accuracy) generalizes to other dimensions (formality, politeness conventions)

**Implications:**
- Customer-facing deployments may need explicit tone guardrails ("remain professional") alongside anti-sycophancy instructions
- Test for register shifts, not just target behavior changes
- The tradeoff between "authentic directness" and "professional register" should be conscious

This is not necessarily a failure — blunter language may be appropriate for some use cases. But it's an uncontrolled effect that deployers should anticipate.

---

## What These Prompts Don't Do

### Don't Replace RLHF/Training

These are runtime interventions. They work within the model's existing capabilities and tendencies. They cannot:
- Fix training-level sycophancy biases
- Overcome strong model priors
- Work if the model lacks capability

They're most effective on capable models with sycophancy as a tendency, not a hard constraint.

### Don't Handle All Contexts

Excluded contexts:
- **Crisis support:** Validation may be appropriate
- **Casual entertainment:** Stakes don't warrant rigor
- **Emotional contexts:** Different framework needed

These prompts are tools, not universal defaults.

### Don't Guarantee Truth

A model with anti-sycophancy prompting can still:
- Be wrong about facts
- Have knowledge gaps
- Make reasoning errors

The prompts address *social* pressure on outputs, not *epistemic* limitations.

---

## Versioning Strategy

### Prompt Versioning

As prompts are refined, maintain version history:
- Major version: Structural changes to principles or protocols
- Minor version: Wording refinements, additional examples
- Date stamps on significant changes

### Model-Specific Adjustments

Different models may need different tuning:
- Some models respond to more explicit instruction
- Some need less philosophical framing
- Token efficiency varies by model

Track which version works best with which model.

### Testing Protocol

When modifying prompts:
1. Define specific behavior to test
2. Create test cases with known "right" answers
3. Compare before/after behavior
4. Watch for regression on other behaviors

---

## Future Considerations

### Potential Additions

- **Education domain:** Correcting without discouraging
- **Medical/health domain:** Accuracy under stakes
- **Legal domain:** Precision in sensitive contexts
- **Sales/persuasion domain:** Ethics of influence

### Integration Patterns

- **Layered injection:** Core + domain-specific
- **Dynamic selection:** Route to appropriate prompt based on context
- **Hybrid modes:** Switch prompts mid-conversation as context changes

### Measurement

- **Sycophancy metrics:** How to measure if it's working
- **User satisfaction:** Does anti-sycophancy hurt engagement inappropriately?
- **Outcome tracking:** Do anti-sycophancy interactions produce better results?

---

## References and Influences

This framework draws on:

- Research on sycophancy in language models (Anthropic, 2023)
- Implementation intention literature (Gollwitzer)
- Say-do gap research in behavioral science
- Falsificationism in philosophy of science
- Commitment devices in behavioral economics

The core insight—that social pressure distorts outputs and that specificity/verifiability counter that pressure—has empirical grounding across multiple disciplines.
