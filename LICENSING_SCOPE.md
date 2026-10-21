# Licensing scope — experimental repository health tool

The MIT licence text at [tools/LICENSE](tools/LICENSE) applies **only** to the
new, separately developed repository-health inventory MVP and its expressly
marked supporting files:

1. `tools/repo_health_check.py`
2. `tests/test_repo_health_check.py`
3. `docs/REPO_HEALTH_CHECK.md`
4. `.github/workflows/repo-health-check.yml`

The Python test file, documentation and workflow have explicit
`SPDX-License-Identifier: MIT` markers referencing the same MIT terms in
`tools/LICENSE`. Changes made to `README.md` for navigation and disclosure
do **not** make the README as a whole MIT-licensed.

**Excluded:** all other files in this mixed-content repository, including
`README.md`, `CASE_STUDY.md`, `METHOD.md`, `EVIDENCE.md`,
`PRIVACY_AND_SCOPE.md`, `SERVICE.md`, `PUBLICATION_CHECKLIST.md`,
`SAMPLE_*.md`, `docs/OSS_READINESS_2026-10-21.md`,
`.gitattributes`, `.gitignore`, and the `assets/*.svg` diagrams.
No licence for those pre-existing materials is granted **by the MVP's MIT
licence**. Any existing rights under law or GitHub's terms are unaffected.

This scope does not include any code or other material from the **private**
OpenTrendIQ-Lite repository. It does not claim ownership of or relicense
upstream GitHub Actions `actions/checkout` or `actions/setup-python`.

**Rights-holder notation:** MIT copyright notice credits Songquan Chen,
the connected account's displayed name. This does not substitute for
independent verification of authorship or third-party content rights.

**Release gate:** This file exists on a publicly readable *draft PR branch*;
the MIT grant for the four listed files should be treated as public once
committed there. It is not approval to merge this PR, create a release, broaden
the licence to historical material, or submit an OpenAI application. Explicit
owner approval is still required before merging.

For a standalone distribution of this tool, prefer extracting the four files
to a dedicated repository, reviewing rights again, and placing an ordinary
MIT `LICENSE` at that new repository's root.
