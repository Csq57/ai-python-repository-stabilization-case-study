# Repository Stabilisation Method

The method is deliberately small:

> Baseline -> boundaries -> reproduction -> evidence -> bounded change ->
> verification -> handover

![The stabilisation sequence](assets/workflow-boundary.svg)

## 1. Establish the baseline

Record the branch, working-tree state, Python version, dependency manager and
documented commands. Do not mix pre-existing defects with changes introduced
during the engagement.

Output: a repository snapshot and a list of assumptions.

## 2. Define boundaries

Write down the workflow being examined, files or modules in scope, protected
interfaces, non-goals, data restrictions and completion conditions.

Output: an agreed phase specification.

## 3. Reproduce current behaviour

Run the documented installation, start, test and build commands where safe.
Capture blockers exactly. Do not hide a broken baseline by changing code before
it is recorded.

Output: reproducible command evidence.

## 4. Prioritise evidence

Identify the five risks with the greatest impact on reliable continuation.
Each finding uses:

> Problem -> Evidence -> Impact -> Recommendation -> Priority ->
> Acceptance Check

Output: a prioritised audit report.

## 5. Make one bounded change

The founding audit includes one small example improvement. It demonstrates how
the recommendation can be applied without turning the audit into a full
refactor.

Output: a reviewable patch or instruction update.

## 6. Verify

Run the agreed checks and compare them with the baseline. Verification should
cover the affected workflow and protected behaviour, not only the new happy
path.

Output: dated results and remaining limitations.

## 7. Hand over

List completed and incomplete work, changed files, commands, evidence, known
risks and the next smallest implementation steps.

Output: a handover that another person or coding agent can follow.

## Operating principles

- Ask for the smallest access level needed.
- Never request live credentials or unredacted customer data.
- Prefer a sanitised copy or agreed read-only access for diagnosis.
- Treat scope changes as separate work.
- Do not present a repository audit as penetration testing, compliance
  certification or legal review.
- Do not promise that a coding agent will stop making mistakes.
