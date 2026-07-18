# Fictional Sample Repository Audit

**Demonstration only.** example-python-service, its commands and every finding
below are fictional. This is a format sample, not evidence about OpenTrendIQ
Lite or a client.

## Executive summary

The example repository can run locally, but its agent instructions do not
identify a single test command or protect the public API. The highest-leverage
improvements are to define the supported environment, make verification
repeatable and prevent partial output publication.

## Repository snapshot

| Field | Fictional value |
| --- | --- |
| Language | Python 3.11 |
| Primary environment | Windows |
| Installation | pip install -e . |
| Test command | python -m pytest -q |
| CI | Present but incomplete |
| Coding-agent instructions | Present but stale |

## Limitations

- No production system or customer data was accessed.
- Network providers were not called.
- The audit is not penetration testing or compliance certification.
- Findings are limited to three fictional workflows.

## Top five risks

### 1. Competing test commands

**Problem:** Documentation gives two different full-suite commands.

**Evidence:** The fictional README uses python -m pytest, while the agent
instructions use pytest tests/unit.

**Impact:** A coding agent can report completion after running only part of the
suite.

**Recommendation:** Select one canonical full-suite command and identify any
intentional subsets.

**Priority:** High.

**Acceptance check:** A fresh checkout uses the documented command and collects
the expected suite.

### 2. Unprotected public interface

**Problem:** The task instructions do not identify the public parser signature
as protected.

**Evidence:** A fictional recent patch changed a positional parameter without a
compatibility test.

**Impact:** A local fix can break callers outside the edited module.

**Recommendation:** Document the protected signature and add a contract test.

**Priority:** High.

**Acceptance check:** The contract test fails when the signature or return shape
changes.

### 3. Partial output can remain after failure

**Problem:** Output is written before validation completes.

**Evidence:** The fictional writer opens the final destination before checking
the required identifier.

**Impact:** Another process may consume an incomplete artefact.

**Recommendation:** Validate first, write to staging and replace the destination
only after success.

**Priority:** High.

**Acceptance check:** Forced validation failure leaves the previous output
unchanged and no staging file remains.

### 4. CI tests only one supported Python version

**Problem:** Project metadata claims two Python versions, while the fictional CI
job exercises one.

**Evidence:** The matrix contains only Python 3.11.

**Impact:** Compatibility defects can reach users of the other declared
version.

**Recommendation:** Align metadata with support policy or expand the CI matrix.

**Priority:** Medium.

**Acceptance check:** CI and package metadata list the same supported versions.

### 5. Agent context includes generated artefacts

**Problem:** Generated output and cache files are included in broad context
selection.

**Evidence:** The fictional task instructions ask the agent to read the entire
working tree.

**Impact:** Relevant source and tests compete with noisy or stale material.

**Recommendation:** Exclude generated directories and name the small set of
files needed for each task.

**Priority:** Medium.

**Acceptance check:** A sample task plan names only source, tests and relevant
instructions.

## Quick wins

1. Publish one canonical verification command.
2. Add protected-interface and non-goal sections to agent instructions.
3. Exclude generated output from default context and version control.

## Fictional 14-day plan

| Days | Activity | Acceptance evidence |
| --- | --- | --- |
| 1-2 | Baseline commands and supported environment | Fresh-checkout run log |
| 3-5 | Parser contract and invalid-input tests | Targeted tests pass |
| 6-8 | Atomic output publication | Failure-path test passes |
| 9-11 | CI and package alignment | Required CI matrix succeeds |
| 12-14 | Instructions and handover | Review checklist completed |

## Recommended next engagement

Implement only the atomic output workflow as a separately scoped change, then
decide whether the remaining findings justify a larger stabilisation sprint.
