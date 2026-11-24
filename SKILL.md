---
name: loop-engineer
description: Design and evolve domain-specific engineering loops with an operator, executor, assessor, and fixer. Use when asked to construct a reusable loop from a domain goal or to run, unblock, stabilize, or optimize one through first success, repeatability, and efficiency, including bounded nested loops.
---

# Loop Engineer

Own the experiment and its progress. Observe the native workflow, intervene at the boundary that limits the current outcome, verify the effect, and return control to the workflow. Preserve existing owners of execution, artifacts, acceptance, and policy. Continue authorized work until the requested stage is verified or no authorized action can advance it.

## Design or evolve a domain loop

When given a domain goal, establish the contract below, discover the native entry points and decision owners, then assemble a reusable domain **Loop Operator** and bind the **Executor**, **Assessor**, and **Fixer** roles. Reuse existing skills, APIs, and checks with suitable contracts. Author a scoped role skill or adapter only for a missing responsibility. Preserve each role's authority and keep the runtime's acceptance owner authoritative. Use [domain loop design and evolution](references/domain-loop.md) for role contracts, assembly, and promotion rules.

When creating or binding a **Fixer**, carry the affected pipeline's semantic contracts into its instructions. Require it to trace the first failed transition, repair the existing owner, or design the smallest missing boundary. If the architecture is implicit, reconstruct the affected path from code and evidence before implementing. Apply the [Fixer contract](references/domain-loop.md#design-and-bind-the-fixer) also when reusing an existing repair capability.

Operate the first loop within authorized scope. After each iteration, decide whether to keep the current composition, change a role skill the Loop Engineer owns, or route a domain/runtime defect to its owner. Stage skill edits as candidates on a fixed acceptance reference and verify the affected handoffs plus the parent outcome before adopting them. The domain Operator runs an adopted composition. The Loop Engineer owns its design and authorized revisions.

## Establish the loop contract

Recover these facts from the request and authoritative project state. Keep the contract in the existing run state when available. Use a compact checkpoint only when resumption requires it.

- **Outcome** — who consumes the result, what decision it enables, and what observable end-to-end evidence qualifies. Identify the workflow entry point, acceptance owner, mandatory gates, and accepted inputs and environment.
- **Starting point** — current baseline, relevant versions/configuration, run IDs, latest accepted checkpoint, and first unresolved boundary. Reuse valid evidence within its scope.
- **Target and evidence paths** — ground both in the current project before choosing a Fixer target or claiming an improvement. Identify the native execution and active implementation for the intended environment, then locate where a trace, test, benchmark, or replay observes or substitutes for it. Use [target and evidence paths](references/domain-loop.md#ground-the-target-and-evidence-paths).
- **Intervention rules** — permitted changes and actors, including what the native workflow must do autonomously. Track external orchestration, required authorization, manual recovery, and native execution in the run evidence. An assisted run qualifies only if the intervention rules allow that assistance.
- **Stopping conditions** — requested stage, repeatability criterion, efficiency target if specified, and shared bounds on elapsed time, spend, attempts, and concurrent work. Derive limits from the user and project. Where absent, state small provisional limits before new work and honor actual resource availability. Treat preliminary criteria as such. Ask the owner only when a missing decision materially changes acceptance, authority, or investment. Advance work common to the viable options while awaiting a decision.

Keep acceptance and its evidence requirements fixed during a comparison. Route changes to the owner, record a new contract version, and reassess which prior evidence still applies. Distinguish feasibility, autonomous operation, repeatability, and economics even if they use the same workflow.

## Run the stage that the evidence supports

| Stage | Optimize for | Exit evidence |
| --- | --- | --- |
| **FIRST_SUCCESS** | Shortest elapsed time to one admissible end-to-end result. Use the native path, spend available parallel capacity on independent critical-path work, and try reversible experiments inside the contract and budget. Capture minimal timing and intervention data now. | One qualifying run from the agreed entry point to the acceptance decision, with traceable evidence and execution ownership. A resumed run qualifies when the contract permits resumption and its full chain is verified. |
| **REPEATABILITY** | Reproduce the result across the agreed operating conditions. Turn relevant failures into bounded reproduction and recovery checks. Speed up time to a dependable result. | The predefined run cohort meets the success and intervention limits, with startup/reset and representative variation covered. Report successes over all eligible attempts, conditions tested, failures, retries, and limitations. |
| **EFFICIENCY** | Improve the requested end-to-end metric under the repeatability and acceptance constraints. Measure, change the limiting step, then measure again. | A comparable baseline/candidate result meets the agreed improvement and guardrails. Verify the candidate on qualifying runs before adoption. If no target was given, report measured gains and stop at the agreed budget or when further gains lack a justified experiment. |

For an underspecified repeatability test, propose a small exploratory cohort with independent starts and representative conditions. Freeze inclusion, thresholds, stop rules, and relevant factors before the runs. Report it as provisional unless it meets the required strength of evidence. Use [repeatability and measurement guidance](references/measurement.md) when defining the cohort or comparing alternatives.

Return to the earliest stage whose evidence the change or regression invalidates. Retain unaffected evidence and keep results from materially different baselines distinct. Start from the highest verified stage compatible with the current contract and baseline. Stop at the requested stage when the user limits scope.

## Operate the loop

1. **Observe.** Read the authoritative job state, traces, relevant artifacts, and agent results. Reconcile any in-flight or uncertain write by run ID, operation identity, and current state before retrying. Let a healthy job continue. While it runs, use the time for independent work only when it can advance the stage or shorten the path after a confirmed issue.
2. **Localize.** Trace expected outcome → last confirmed good boundary → first observed bad boundary → owning contract. Mark facts, hypotheses, external unknowns, and missing authority. If causality is uncertain, choose the cheapest discriminating observation before assigning a fix. Confirm which path the evidence exercised and whether the violated property belongs to a shared contract, the selected implementation, or the evidence mechanism. Check known downstream gates to avoid knowingly stopping one gate later.
3. **Challenge necessity.** Name the consumer and the incorrect decision or failed outcome this work prevents. Separate the required property, the evidence sufficient to establish it, and the current mechanism. Consider existing evidence, deleting the work, or moving it to the owner. When material uncertainty remains, use the project's architecture and simplification review if available. Keep unrelated findings out of the active work queue.
4. **Intervene.** Prefer the native operation. Restore an unavailable environment through its owner. Route a confirmed local defect to the existing owner with targeted acceptance. Use capability repair when an existing owner repeatedly cannot meet a justified contract. Escalate normative ambiguity to the decision owner. Use the project's normal review, integration, and validation paths. Record the predicted observable change and how the result would change the next decision.
5. **Verify and resume.** Compare expected and observed results. For delegated changes, check the accepted output and integration baseline. For a Fixer change, check the owning boundary, preserved guarantees, and the unchanged end-to-end acceptance contract before adopting it. Report validation at the scope actually exercised and name any unverified target path. Resume the original workflow at the earliest valid checkpoint and confirm that its acceptance frontier advanced. A fix or accepted patch is an intermediate result until the active run demonstrates the effect.

Track the frontier as the last admissible outcome and the next unsatisfied acceptance condition. Engineering activity and product progress are distinct.

When progress is unclear, have the Assessor compare the blocking condition across attempts using evidence applicable to each candidate. Identify whether the same obligation remains open, a prior one was resolved and exposed another, or a previously satisfied one reopened. If the evidence cannot distinguish these cases, obtain the smallest observation that changes the next decision. If an allowed action demonstrably cannot affect the blocker, route directly to the owner who can.

After two materially different interventions with no frontier movement, or sooner if the same failure or ownership dispute recurs, revisit the goal, owning contract, and need for the work. Choose native execution, focused repair, removal, acceptance of the limitation, or an investment decision. Retry only when relevant inputs, conditions, or the observation change, or when the repeatability protocol calls for a fresh independent run.

## Delegate and nest

Use an ordinary worker for a bounded task with a known method and acceptance check. Start a child Loop Engineer only when an active blocker has its own observable acceptance, needs iterative investigation or repair, and the parent can say exactly what it will do with the accepted result.

- **Parallel dispatch.** Launch independent work when inputs are ready and it shortens the critical path or distinguishes competing hypotheses faster. Give each worker an owner, baseline, scoped writes, acceptance evidence, and reporting deadline. Keep overlapping writes serialized or isolated under one integration owner. Keep dependent implementation queued until its input is known. Cancel redundant branches safely once their result cannot change the decision. Count their incurred cost.
- **Child contract.** Pass parent loop/run ID, blocker evidence, one outcome and its oracle, baseline, authorized scope, resource allocation, target stage, and stop/return conditions. Default the child to one admissible result unless the parent's blocked decision requires repeatability or efficiency evidence. The parent owns the parent verdict and remains accountable for integration.
- **Bounded recursion.** The root sets a finite shared budget and depth. Default to one nested level unless deeper nesting is justified and explicitly budgeted by the root. Reserve capacity before launch, charge descendant attempts and spend to the root, and clamp child deadlines and authority to the parent's. Prevent ancestor dependency cycles, duplicate active blocker work, and concurrent writes to the same owned state. Release any execution slot a waiting parent holds if its child needs that slot to run. If the runtime has no delegation, run the bounded work serially or use its native task facility.
- **Return and rejoin.** The child returns status, evidence references, accepted baseline, intervention record, resource used, and remaining blocker or exact resume point. Verify the receipt against the current parent baseline, integrate through the designated owner, and rerun the parent boundary. Expired, stale, or uncertain results require reconciliation. A child can unblock a parent without satisfying the parent's acceptance.

## Checkpoint and report

Use canonical workflow state. Keep only additional facts needed for decisions or recovery: stage, acceptance frontier, run IDs and baseline, active operations and their owners, evidence, remaining budget, and next action. When resuming after interruption, reconcile active operations and check baseline changes before issuing new actions.

In updates and at handoff, lead with the current decision and frontier. State the first bad boundary and evidence, why it matters to the consumer, one next action with owner and acceptance, and where the native workflow resumes. Mention parked findings only if relevant. At exit report the verified stage, qualifying evidence and scope, actual intervention and cost, and any exact blocker or stop condition. Use a real result or checkpoint to support a claim of progress.
