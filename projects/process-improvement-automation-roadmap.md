[← Back to Home](../)

---

# Manufacturing Process Improvement — Test & Programming Automation

**Context:** Sanitised case study based on workflow observation in an Electronics Manufacturing Services (EMS) environment with repeated programming and test steps, frequent product changeovers, and multiple PCB variants.

This project summarises a practical improvement proposal focused on reducing repeated setup loss, improving repeatability, strengthening traceability, and introducing targeted automation where the workflow is repetitive enough to justify it.

Company-specific details have been removed.

---

## Why this project matters

This work is relevant because manufacturing performance is shaped not only by whether a board passes test, but by whether the overall workflow can be repeated reliably, configured correctly for each variant, and improved using real data rather than guesswork.

The value of this case study lies in translating shop-floor observation into a staged improvement plan that targets the sources of everyday friction: repeated setup, task switching, fragmented logging, variant-selection errors, and hidden bottlenecks.

---

## Problem Pattern Observed

Several recurring issues were visible in the workflow:

- repeated setup and frequent movement between jobs or stations added hidden time and increased the chance of mistakes
- troubleshooting depended too heavily on a small number of experienced individuals, creating delays when faults occurred
- paper-based or fragmented logging made it difficult to trace recurring issues or measure improvement properly
- multiple PCB variants, firmware versions, and product options increased the risk of incorrect settings
- fragmented “one order at a time” flow created stop-start behaviour, extra changeovers, and reduced throughput
- limited visibility of incoming PCB availability meant that local improvements could easily be blocked by upstream constraints

These were not isolated technical faults, but repeatable process weaknesses affecting throughput, consistency, and resilience.

---

## Proposed Improvement Approach

### Phase 1 — Stabilise and Measure

- standardise station setup and working method using short, visual, version-controlled instructions
- replace paper-heavy recording with lightweight digital traceability, including QR or barcode-based job and station logging
- define golden-sample references and clear escalation rules for abnormal results
- introduce simple digital checklists so critical steps and pass/fail criteria are applied consistently
- create a baseline dataset for setup time, faults, repeat issues, and throughput before heavier automation is introduced

### Phase 2 — Reduce Repeat Errors and Setup Loss

- introduce programming and test profiles for PCB variants so the correct settings can be selected quickly and consistently
- reduce manual configuration choices by linking scanned IDs to the correct workflow, firmware, or variant profile
- batch work by PCB family where practical to reduce repeated preparation and station hopping
- use simple sequencing rules to complete boards requiring the same fixture or profile before switching
- improve repeatability with fixtures, more consistent cable/connector arrangements, and better station organisation

### Phase 3 — Expand Automation and Protect Flow

- automate the most repetitive and measurable stations in stages, starting from validated baseline procedures
- extend automation concepts across programming and electrical test where repeatable measurement sequences can be logged automatically
- consider PC-controlled test execution for defined sequences such as stepped-voltage PSU board testing
- strengthen flow visibility across departments by tracking WIP, blockers, PCB availability, and expected arrivals
- use the collected data to identify where the bottleneck shifts once local throughput improves

---

## Why this approach was chosen

The proposal deliberately starts with **measurement, traceability, and standardisation** rather than jumping straight into large-scale automation.

That choice matters because automation works best when the existing process is already stable enough to be repeated, measured, and debugged. In this case, the first priority was to reduce ambiguity, remove avoidable manual friction, and build enough structured data to support later decisions with evidence.

The proposal also recognised that improving one station in isolation can simply move the bottleneck elsewhere. For that reason, flow visibility and PCB availability were treated as part of the improvement logic rather than as a separate planning issue.

---

## Example Improvement Themes

### Digital Traceability Instead of Paper

A lightweight digital work-order approach was proposed so that progress, measurements, and pass/fail outcomes could be recorded consistently at each station.

This would help to:

- reduce transcription errors
- make audits easier
- build structured historical data for recurring faults and process trends
- quantify whether changes are genuinely improving throughput or just moving the problem

### Profile-Based Execution for Variants

A profile-driven approach was proposed for boards with similar test flow but different firmware, thresholds, or options.

This would help to:

- reduce wrong-setting and wrong-variant errors
- shorten changeovers between similar products
- ensure the same logic is applied every time
- make automation more scalable across multiple board families

### Automation Where the Sequence is Repetitive

Automation was proposed only where the process is repetitive, measurable, and stable enough to benefit from it.

Examples included:

- profile-driven programming steps for repeated board types
- automated electrical measurement sequences with logging and pass/fail evaluation
- PC-controlled PSU board testing based on a defined voltage-stepping and threshold-check sequence

The aim was not automation for its own sake, but consistent execution and cleaner datasets.

### Flow Visibility and Bottleneck Protection

The proposal also recognised that faster output in one department is only useful if upstream PCB supply can support it.

For that reason, flow visibility was treated as important:

- WIP by station
- blocked jobs
- PCB availability
- expected arrivals
- visible bottlenecks before the line runs dry

This helps prevent the classic factory nonsense where you “improve” one area only to discover you have simply converted working time into waiting time.

---

## Expected Operational Impact

If implemented well, this approach would be expected to improve the workflow in several practical ways:

- fewer wrong-setting and wrong-variant errors
- reduced setup time and less context switching
- more repeatable programming and test execution
- faster troubleshooting through structured logs and clearer failure history
- lower dependency on a small number of experienced individuals
- better onboarding and more predictable shift-to-shift performance
- improved visibility of blockers and bottlenecks across departments
- stronger basis for future automation justified by measured results

Quantitative savings would depend on baseline data collection, which is why the first phase focuses explicitly on making the workflow measurable.

---

## My Contribution

- observed the workflow at station level and identified repeated friction points affecting throughput and consistency
- translated those observations into a phased improvement strategy rather than a one-step “automate everything” proposal
- identified batching by PCB family and reduced station switching as practical opportunities to recover hidden time
- proposed lightweight digital traceability using job-level records and QR/barcode-linked station logging
- identified profile-based execution for PCB variants as a practical way to reduce wrong-setting errors and shorten changeovers
- highlighted the value of standard work, digital checklists, golden-sample references, and clear escalation rules
- considered flow visibility beyond the station itself, recognising that local improvements can shift the bottleneck upstream if PCB availability is not made visible

---

## Engineering Takeaways

- process repeatability matters as much as technical correctness in a production environment
- standardisation and measurement should come before heavier automation
- profile-based execution is a practical way to improve variant control without adding unnecessary complexity
- lightweight digital traceability can expose recurring faults, trends, and bottlenecks far more effectively than paper records
- improving one station is not enough if upstream flow cannot sustain the higher output
- engineering judgement in manufacturing often means removing ambiguity, reducing avoidable human error, and making performance measurable
