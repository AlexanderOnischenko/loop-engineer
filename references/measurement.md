# Repeatability and end-to-end measurement

## Define an admissible run

Choose the unit the consumer actually accepts. Pin relevant versions, workload, limits, and environment. Record start/end, run ID, verdict and evidence, phase timing, queue and human wait, retries, and resource usage. Distinguish all started runs from eligible completed runs. Predetermine rules for exclusions and publish counts for exclusions, cancellations, timeouts, and unresolved outcomes. Preserve failed attempts in cost and incident accounting. Define how timeouts enter the success denominator and report indeterminate outcomes separately when the final effect remains unknown.

## Test repeatability

Use fresh starts with explicit reset rules or independent work units. Probe factors that can change the result, such as seed, case class, worker, cache state, contention, or permission state, where relevant and authorized. Replays on a single seed, cache, or environment establish that narrower claim. Check ordinary repeats and recovery separately if both are in scope. Define confidence/precision and sample requirements for reliability claims that affect consequential decisions. With a small cohort, report counts and limits of inference. Several consecutive green runs can be an engineering gate, with the claim restricted to the actual cohort.

## Measure efficiency

Choose one primary metric aligned to the decision. Examples include elapsed time to an accepted result, cost per accepted result including failed and speculative attempts, throughput of accepted cases, and operator minutes. Declare reliability, quality, and intervention guardrails and the stop or rollback signal before the trial. Report percentiles only with enough observations to interpret them. When useful, show queue versus execution, critical-path waits, and rework. Compare matched workload and resource conditions with the same oracle. Alternate, pair, or randomize baseline and candidate trials when time or shared resources could bias the comparison. Use a small reversible trial when risk or variance warrants it. If the candidate violates an acceptance or reliability guardrail, keep or restore the last qualifying baseline through the existing path and determine which stage needs new evidence.

## Worked example — autonomous delivery

A parent seeks one BCU closure with qualified evidence and native controller ownership. An admission failure reports stale regression bindings. Inspect which binding first disagrees with the candidate baseline, whether the binding remains required, and whether a native refresh route applies. Use native recovery if the contract permits it. If a confirmed controller routing defect blocks it, give a child loop the outcome “the controller requests the owning binding refresh and resumes admission on the failing input.” The binding producer retains ownership of the binding. The parent accepts the repair through the normal path, then resumes Verify and checks the original BCU closure and intervention record. An operator-performed required controller step would invalidate an autonomy claim when the run forbids that intervention. Claims about repeatability require additional qualifying runs under a defined cohort.

## Sources

- Mike Rother, *Toyota Kata*. Apply the target-condition and experiment pattern by writing the prediction and inspecting the actual effect. [Toyota Kata excerpt](https://www.lean.org/wp-content/uploads/2022/04/toyota_kata.pdf)
- Goldratt Research Labs, *What is Theory of Constraints?*. Reidentify the limiting constraint after each material intervention. [Five focusing steps](https://www.goldrattresearchlabs.com/pdf/What_is_Theory_of_Constraints_%28TOC%29.PDF)
- NIST/SEMATECH, *Assessing Process Stability*. Match the stability claim to the process variation and the quantity and independence of observations. [Engineering Statistics Handbook](https://itl.nist.gov/div898/handbook/ppc/section4/ppc45.htm)
- Google, *The Site Reliability Workbook*. Compare candidate and baseline and include relevant failure and performance metrics in a bounded trial. [Canarying Releases](https://sre.google/workbook/canarying-releases/)
