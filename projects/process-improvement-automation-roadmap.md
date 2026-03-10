[← Back to Home](../)

---

# Manufacturing Process Improvement — Test & Programming Automation

**Context:** Electronics Manufacturing Services (EMS) environment with repeated programming and test steps across multiple product variants.

This case study summarises a practical improvement proposal based on real workflow observation in a production setting. The focus was on reducing setup friction, improving repeatability, and introducing enough traceability to support better day-to-day decisions without overcomplicating the process.

Company-specific details have been removed.

---

## Why this project matters

This work is relevant because good engineering in manufacturing is not only about passing a test once. It also depends on whether programming and test steps can be repeated reliably, whether the correct variant is selected every time, and whether common failure patterns can be traced and improved.

The value of this case study lies in identifying practical sources of friction and proposing realistic improvements that could be introduced in stages.

---

## Problem Pattern Observed

Several repeatable issues were visible in the workflow:

- repeated station setup and frequent task switching increased the chance of mistakes and slowed throughput
- troubleshooting and decision-making depended too heavily on a small number of experienced individuals
- paper-based or fragmented logging made it difficult to quantify recurring faults or measure improvement over time
- handling multiple variants, firmware versions, and product options increased the risk of incorrect settings

These were not isolated technical faults, but recurring process-level weaknesses.

---

## Proposed Improvement Approach

### Phase 1 — Stabilise and Measure

- standardise station setup and working method using simple checklists and visual aids
- introduce lightweight digital logging, including QR-based traceability, to establish a usable baseline dataset
- define golden-sample references and a clear escalation path for faults that cannot be resolved locally

### Phase 2 — Reduce Repeat Errors

- introduce profile-driven programming steps for different variants
- reduce manual configuration choices by linking scanned IDs to the correct settings
- improve repeatability with fixtures and more consistent connections where appropriate

### Phase 3 — Expand Visibility and Automation

- extend successful automation concepts to additional stations once stable
- improve visibility of work in progress, blockers, and priorities using simple shared logs or dashboards
- iterate based on measured bottlenecks and real recurring failure modes

---

## Why this approach was chosen

The proposal deliberately starts with **measurement and standardisation**, rather than jumping straight into heavier automation.

That matters because automation is most useful when the underlying process is already stable enough to measure, repeat, and debug. In this case, the first priority was to reduce ambiguity, make common problems visible, and create a baseline that later improvements could be judged against.

---

## Expected Operational Impact

If implemented well, this approach would be expected to improve the workflow in several practical ways:

- fewer wrong-setting and wrong-variant errors
- reduced setup time and less operator context switching
- lower dependency on specific individuals for routine decisions
- better historical traceability for recurring faults and process bottlenecks

Quantitative savings would depend on baseline data collection, which is why the first phase focuses explicitly on making the workflow measurable.

---

## My Contribution

- observed the workflow at station level and identified repeated friction points
- translated those observations into a phased improvement plan
- prioritised practical actions rather than high-complexity automation from the start
- defined realistic deliverables such as standard work, traceability steps, profile-based execution, and fixture opportunities

---

## Engineering Takeaways

- process repeatability matters as much as technical correctness in a production environment
- lightweight traceability can unlock much better decisions without requiring a full complex MES rollout
- automation works best when it is introduced on top of a stable, measurable workflow
- engineering judgement is often about reducing ambiguity and preventing avoidable errors before they happen
