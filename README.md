# Loop Engineer

Loop Engineer is a Codex skill for turning a domain goal into a reusable engineering workflow. It assembles a domain-specific Loop Operator, runs the workflow within the authority you grant, and uses evidence from each run to improve the next one. Use it for delivery, verification, builds, evaluations, or other workflows with an observable acceptance decision.

## Install in Codex

From the root of the project where you want to use the skill:

```sh
mkdir -p .agents/skills
git clone https://github.com/AlexanderOnischenko/loop-engineer.git .agents/skills/loop-engineer
```

For use across projects, clone it into `~/.agents/skills/loop-engineer` instead. Keep the entire folder so Codex can load the references and UI metadata. See the [Codex skill discovery documentation](https://learn.chatgpt.com/docs/build-skills#where-codex-loads-local-skills).

## Run your first loop

Open Codex in the target project and explicitly invoke `$loop-engineer`. Give it the domain goal, the evidence that qualifies, the desired stage, and the scope of authorized changes. Include the native entry point or any existing role skills if you know them.

```text
Use $loop-engineer to design and run a reusable invoice-batch delivery loop.

Goal: Deliver one batch that the existing auditor accepts after the native
runner submits it. The runner owns recovery and resume. Manual overrides
invalidate the autonomy claim.

Use the existing submit/resume commands, the auditor's verdict API, and
the billing team's recovery workflow. Save the Loop Operator in this project.

Scope: Staging only. You may edit skills created for this loop and run the
existing workflow. Budget: 30 minutes and up to two workers.
Stop at the first accepted end-to-end result and show its run ID and verdict.
```

For design only, say “create the Loop Operator and its role bindings, then stop before execution.” For an existing run, provide its ID, the last confirmed checkpoint, and the target stage. For an efficiency experiment, give a measurable target such as “reduce median time to accepted batch by 20% under the existing repeatability and acceptance criteria.”

## How the workflow is composed

| Role | Responsibility |
| --- | --- |
| **Loop Operator** | Starts or follows the run, asks for assessment, routes confirmed blockers, and resumes the original workflow. |
| **Executor** | Uses the native execution path and returns run IDs, observations, and evidence. |
| **Assessor** | Applies the accepted contract, retrieves canonical verdicts, and localizes failures. |
| **Fixer** | Traces the first failed semantic transition, repairs or designs its owning boundary, and returns validation evidence and a resume point. |

Loop Engineer reuses suitable skills, APIs, and deterministic checks. It authors a role skill or adapter when a responsibility is missing. A blocker with its own acceptance criterion and an iterative repair process can get a bounded child loop that shares the parent's budget.

### How the Fixer works

The Fixer traces the affected path from native input to acceptance. At each stage it identifies the input guarantees, the property that stage establishes, and the properties it preserves. It repairs the first violated transition at its owner. If no stage owns a required property, the Fixer designs the smallest missing boundary and connects its producer and consumer.

For JSON repair, this could mean tracing candidate selection, recognition of strings and structural delimiters, and strict decoding. The repair belongs where its preconditions can be verified. The acceptance check still compares the decoded values and rejects inputs outside the supported repair scope.

## Advance the evidence

1. **First success.** Verify one end-to-end outcome against the agreed contract and record who performed each required action.
2. **Repeatability.** Run the predefined cohort with fresh starts and representative conditions. Track failures, retries, timeouts, and interventions.
3. **Efficiency.** Compare baseline and candidate on the same end-to-end metric, with acceptance and reliability constraints in force. Revisit earlier stages if a regression invalidates their evidence.

After each iteration, Loop Engineer can propose an edit to an owned role or handoff. In-flight runs keep their original versions. A candidate is evaluated against the same acceptance rules using the failing case, a previously accepted case, and a relevant negative case. Changes to the Assessor need an independent expected verdict or authoritative check. Changes to what qualifies as success go to the contract owner and establish a new baseline.

Read the [skill instructions](SKILL.md), [role and revision guidance](references/domain-loop.md), or [measurement guidance](references/measurement.md).
