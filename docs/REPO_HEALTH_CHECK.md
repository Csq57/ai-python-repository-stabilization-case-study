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


--fail-on warning exits with status 1 when at least one required check is missing. The default is observational and exits 0 for valid directory scans. Invalid directories exit 2.

## What it reports

The tool checks for a README, explicit licence file, Python package metadata, a GitHub Actions YAML workflow, Python test modules, optional contributing instructions and optional security reporting policy. It excludes common generated folders and does not follow directory symlinks while looking for tests. A scan of more than 20,000 files may report an incomplete search.

## Boundaries

- It **never runs project code** and **never invokes an external service**.
- It does not analyse source-code correctness, actual workflow success, packaging reproducibility, dependencies, legal copyright ownership or vulnerabilities.
- A file's presence **does not prove** its validity or quality.
- Public GitHub visibility **does not confer** an open-source licence. Licence choice and publication require project-owner review.
- It does not provide any claim of ChatGPT Pro eligibility or OpenAI endorsement.
- It does not inspect private source repositories or client records.

## Maturity

Experimental MVP. No independent users, downloads, or adoption claims have been established. The tool and tests are proposed as a draft pull request for review and should not be represented as a production-ready product.
