# Design and evolve a domain loop

## Assemble the smallest runnable composition

1. Turn the domain goal into one unit of accepted work, one qualifying observation, and a named decision owner. For multiple success claims, state their order and evidence separately. For example, native autonomous BCU closure precedes a claim about faster autonomous closure.
2. Inventory the normal execution, evaluation, and recovery entry points. Bind working responsibilities at their existing boundaries. Use a thin adapter for a genuine input/output mismatch. Create an owned role skill when a recurring domain decision lacks an implementation. A native API, deterministic test, or existing skill can fill a role.
3. Save a reusable domain Operator skill when the user requests a reusable loop. In its repository-native format record the loop contract reference, versioned role bindings, permitted decisions and retries, evidence paths, and how to start or resume. Separate role skills only when they need their own lifecycle or reuse. Use the requested authoring or install scope and the project's existing state. If the user also authorizes execution, run an initial case through the normal entry point. Report design, installed composition, and verified outcomes according to what occurred.

## Preserve the role contracts

| Role | Input | Result and authority |
| --- | --- | --- |
| **Loop Operator** | Goal, contract, active composition, run or resume state | Start or follow execution, ask for assessment, route necessary fixes, and rejoin the original run. Publish workflow status from canonical evidence. |
| **Executor** | Work unit, pinned inputs, permitted execution or resume action | Run via the native entry point. Return run ID, observed outcome, artifacts/evidence, and interventions. |
| **Assessor** | Run evidence and its baseline, versioned acceptance rules | Return accepted, failed, or indeterminate with evidence and reason. Identify the first bad boundary and route, invoking specialist review as needed. Consume canonical verdicts at their owning boundary. |
| **Fixer** | Validated blocker, owning contract, allowed writes, targeted acceptance | Return a proposed or integrated repair with validation evidence and a rejoin point. Invoke the appropriate owner when the change sits outside its authority. |

The Assessor owns the assessment only where delegated. Acceptance criteria come from their normative owner. An Executor or Fixer may provide checks and diagnostics, while approval of their work comes from the designated assessment path. If no independent acceptance path exists, use deterministic evidence or report the resulting claim as provisional. Existing mandatory reviews remain in force.

For SDLC Lens, bind the Executor to native BCU operations. Let the Assessor consume the canonical verification and assurance verdicts and invoke `architecture-review-guard` when a finding challenges a mechanism or an ownership boundary. Bind the Fixer to the relevant recovery or delivery owner, such as capability delivery for a confirmed platform gap. The Operator follows the job and rejoins it after repair. Use a nested Operator only when the blocker has its own outcome and requires a loop, as described in the main skill.

## Change a composition between runs

1. **Diagnose before rewriting.** Use the observed handoff and the first bad boundary to distinguish faulty skill instructions, a broken interface, a domain/runtime defect, and missing authority. Prefer using or simplifying an existing responsibility. Tie any skill edit to a failure or measurable opportunity and state the predicted change.
2. **Pin the active version.** Keep one active composition for an in-flight run and reconcile its operations before replacement. Pin the contract, role versions, and evidence protocol. Edit one owning role or handoff at a time where possible. If a shared interface requires coordinated edits, version and test them as one candidate with an explicit compatibility or migration path. Keep sibling and parent compositions pinned until their owners adopt the new binding. Keep shared skills owned by their maintainers and route proposed changes there.
3. **Verify the candidate.** Retain the failing case, a previously accepted case, and a relevant negative case. For changed handoffs, check both sides and the parent path. Assess baseline and candidate under the same externally anchored oracle. When changing the Assessor, test against fixed expected verdicts, including a plausible false pass, and use the authoritative checker or independent review for promotion. New verdicts from the candidate Assessor alone cannot validate that Assessor.
4. **Promote or retain.** Adopt the whole candidate version only after affected checks and the required parent stage pass. Apply the smallest evidence requirement that supports the claim. Reassess earlier stages affected by the change. If the candidate fails, retain or restore the prior composition and record the reason. Reconcile any external side effects separately. Keep an exact version and resume point. The next iteration may revise another skill if its evidence justifies it.

Routine instructions, routing, and mechanics may evolve within delegated authority. Changes to the goal, acceptance threshold, oracle semantics, mandatory gates, autonomy boundary, or permissions require the corresponding contract owner and a new experimental baseline. Work within the return and budget rules for children. The Loop Engineer edits skills it owns for the domain loop. Changes to the Loop Engineer itself are a separate skill revision.
