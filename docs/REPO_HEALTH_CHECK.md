<!-- SPDX-FileCopyrightText: 2026 Songquan Chen -->
<!-- SPDX-License-Identifier: MIT -->

# Repository health inventory — experimental MVP

This is a standalone, zero-dependency Python 3.11+ tool demonstrating a *read-only* repository-maintenance inventory. It was newly written for this public case-study repository, not copied from the private OpenTrendIQ product.

## Quick start

From the repository root:

```shell
python tools/repo_health_check.py .
python tools/repo_health_check.py /path/to/your/repo --format json
python tools/repo_health_check.py . --fail-on warning
python -m unittest discover -s tests -p 'test_repo_health_check.py' -v
```


`--fail-on warning` exits with status 1 when at least one required check is missing **or test-file scanning is incomplete**. The default is observational and exits 0 after producing a valid inventory, even when warnings exist. Invalid or inaccessible root directories exit 2.

## What it reports

The tool checks for a README, explicit licence file, Python package metadata, a GitHub Actions YAML workflow, Python test modules, optional contributing instructions and optional security reporting policy. It excludes common generated folders and does not follow directory symlinks while looking for tests. It caps traversal at 20,000 files and 5,000 directories. If any scanned directory is unreadable, or a scan limit is exceeded before a test is found, it reports **Incomplete search** rather than saying tests are absent. Packaging metadata is informational rather than required: many Python projects are intentionally un-packaged scripts.

## Boundaries

- It **never runs project code** and **never invokes an external service**.
- It does not analyse source-code correctness, actual workflow success, packaging reproducibility, dependencies, legal copyright ownership or vulnerabilities.
- A file's presence **does not prove** its validity or quality.
- The test inventory checks filenames only; it does not guarantee tests can run or that all repository files were inspected after finding a test.
- JSON output includes the absolute scanned filesystem path. Redact this field before publicly sharing logs if the local path is sensitive.
- Public GitHub visibility **does not confer** an open-source licence. Licence choice and publication require project-owner review.
- It does not provide any claim of ChatGPT Pro eligibility or OpenAI endorsement.
- It does not access private remote repositories or client records itself; **a directory path supplied by the user can still refer to local private files or a network mount**, so only scan paths you are authorised to inspect.

## Maturity

Experimental MVP. No independent users, downloads, or adoption claims have been established. The tool and tests are proposed as a draft pull request for review and should not be represented as a production-ready product.

## Licensing

This MVP is licensed under the MIT terms at [tools/LICENSE](../tools/LICENSE),
subject to the explicit [licensing scope](../LICENSING_SCOPE.md). Only the
four enumerated newly developed tool-related files are covered. Existing
case-study documents and diagrams are **not** automatically MIT-licensed.
