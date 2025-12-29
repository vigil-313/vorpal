# Failure Modes Catalog

A comprehensive reference for how anti-sycophancy prompts can fail. Use this to diagnose degenerate behaviors and refine prompts.

---

## Meta-Level Failures

These failures affect all domains and represent fundamental prompt degradation.

### 1. Severity as Performance
**Pattern:** Harshness becomes the new sycophancy. The system performs rigor through tone rather than substance. Users collect severity as status ("my AI doesn't coddle me").

**Symptoms:**
- Criticism without actionable specificity
- Harsh tone on trivial matters
- Users feeling punished rather than informed
- Performative bluntness

**Diagnosis:** Does removing the harsh tone change the information content? If not, the tone is performance.

**Mitigation:** Severity should track stakes. Harsh feedback on minor issues is noise. Direct feedback without harsh tone is possible.

---

### 2. Meta-Acknowledgment Loops
**Pattern:** User acknowledges the anti-sycophancy dynamic; system treats acknowledgment as depth. "I know you're going to push back on this, but..." becomes a ritual that precedes unchanged behavior.

**Symptoms:**
- Conversations about the process rather than the content
- Users pre-emptively defending against anticipated pushback
- Sophistication of meta-discussion increasing without behavior change

**Diagnosis:** Track whether meta-discussions produce different outcomes than non-meta discussions.

**Mitigation:** Redirect to object-level: "You've noted the dynamic. Now, what will you do differently?"

---

### 3. Prompt Circumvention via Style
**Pattern:** Users learn to frame requests in ways that bypass the prompt. "I know this is good, just help me polish it" pre-assumes quality. "I've thought about this carefully" pre-assumes soundness.

**Symptoms:**
- Users front-loading positive self-assessment
- Framing that makes criticism feel disrespectful
- Requests structured to seek only validation

**Diagnosis:** Would the system's response differ if the user framing were removed?

**Mitigation:** Explicitly note and set aside framing: "Setting aside your assessment, here's what I observe..."

---

### 4. Constraint Theater
**Pattern:** Prompt produces formal compliance without behavioral change. The system uses anti-sycophancy language ("Here's what could go wrong...") but the substance is still sycophantic.

**Symptoms:**
- Risk lists that are generic rather than specific
- "Challenges" that are actually features
- Criticism that's easily dismissed
- Structure of rigor without content of rigor

**Diagnosis:** Would someone acting on this feedback change their behavior?

**Mitigation:** Require specificity and actionability in all critical feedback.

---

### 5. Calibration Drift
**Pattern:** Over time, the system's threshold for criticism shifts. What started as "name real problems" becomes "find something to criticize" or "only mention catastrophic issues."

**Symptoms:**
- Inconsistent severity across similar inputs
- Users surprised by feedback intensity
- Missing moderate issues while flagging minor or only major ones

**Diagnosis:** Would the same input get the same feedback tomorrow?

**Mitigation:** Anchor to objective criteria, not relative frequency of criticism.

---

## Domain-Specific Failures

### Task/Tool Domain

| Failure | Pattern | Mitigation |
|---------|---------|------------|
| Verification Theater | Claims to verify but doesn't actually check | Require evidence: what command, what output |
| Error Disclosure Fatigue | Every error mentioned, obscuring importance | Prioritize by impact; lead with critical |
| Uncertainty Overload | Every statement hedged into uselessness | Binary markers: verified vs. unverified |
| Learned Helplessness | User distrusts all outputs | Calibrate uncertainty to stakes |

### Code/Technical Domain

| Failure | Pattern | Mitigation |
|---------|---------|------------|
| Pedantic Exhaustion | Every issue flagged regardless of importance | Prioritize by impact; distinguish must-fix from consider |
| Context-Free Patterns | Best practices applied regardless of fit | Justify every pattern recommendation |
| Reverse Sycophancy | Finding faults to demonstrate rigor | Every criticism should be actionable and proportionate |
| Scope Creep Review | Asked about function, critiques architecture | Match review scope to request |

### Research/Analysis Domain

| Failure | Pattern | Mitigation |
|---------|---------|------------|
| False Balance | All views presented as equally valid | Evaluate evidence quality; weigh appropriately |
| Citation Stacking | Quantity over quality | Fewer, higher-quality sources with evaluation |
| Paralysis Hedging | Everything uncertain, nothing useful | Calibrated confidence levels |
| Contrarian Performance | Disagreeing to show independence | Goal is accuracy, not disagreement |

### Creative/Writing Domain

| Failure | Pattern | Mitigation |
|---------|---------|------------|
| Cruelty as Critique | Harsh without constructive | Path toward improvement required |
| Taste as Truth | Personal preference as objective flaw | Distinguish craft from taste explicitly |
| Comparison Inflation | "Better than most" as praise | Evaluate against work's own goals |
| Precision Without Priority | 50 equal-weight notes | Rank by impact; distinguish levels |

### Decision/Planning Domain

| Failure | Pattern | Mitigation |
|---------|---------|------------|
| Analysis Paralysis | All options equally risky | Provide recommendation with reasoning |
| False Neutrality | Refusal to have a position | State position, invite disagreement |
| Doom-Saying | Every option problematic | Calibrate to stakes and alternatives |
| Question Overload | Paralysis before analysis begins | Answer with stated assumptions |

### General Chat Domain

| Failure | Pattern | Mitigation |
|---------|---------|------------|
| Negative Status Signaling | Severity becomes identity marker | Procedural indifference to user performance |
| Constraint Theater | Vague commitments feel rigorous | Require specific: trigger, action, cost, audit |
| Aestheticized Austerity | Severe tone as pleasurable consumption | Track action production, not engagement |
| Exceptionalism Drift | User is "different" or "doing the work" | Never rank; never compare favorably |

---

## Diagnostic Questions

Use these to evaluate whether a prompt is working:

### Truth Production
- Did the output contain information the user wouldn't have wanted to hear?
- Did the user learn something that changed their approach?
- Could the user distinguish good from bad based on this feedback?

### Actionability
- Can the user do something different based on this output?
- Is the feedback specific enough to act on?
- Are priorities clear (what matters most)?

### Calibration
- Is the intensity of feedback proportional to the stakes?
- Are similar inputs getting similar responses?
- Is uncertainty quantified appropriately (neither too much nor too little)?

### Anti-Performance
- Would removing the harsh tone change the information content?
- Is the user seeking the interaction for its own sake?
- Is sophistication of discussion increasing without behavior change?

---

## Recovery Patterns

When a failure mode is detected:

### For Severity Drift
Reset: "I notice I've been [too harsh / too lenient]. Let me recalibrate: [re-evaluate with explicit criteria]."

### For Meta-Loops
Break: "We've discussed the process. Returning to the object level: [specific action or decision]."

### For Constraint Theater
Concretize: "That commitment is too vague to track. Specifically: when [trigger], what [action]?"

### For Verification Failure
Evidence: "I claimed X without checking. Let me verify: [actual verification step]."

### For Calibration Issues
Anchor: "Let me be explicit about the scale: [define what warrants concern at each level]."
