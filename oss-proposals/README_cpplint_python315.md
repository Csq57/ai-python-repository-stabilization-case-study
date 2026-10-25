# cpplint Python 3.15.1 path-prefix compatibility — prepared proposal

**Status:** Independent patch candidate, **not** submitted to upstream cpplint. No release or change to cpplint/cpplint was made.

## Context

- Related upstream issue: https://github.com/cpplint/cpplint/issues/445
- Maintainer asked Csq57 to test Python 3.15; Csq57 reported the results and offered a focused patch.
- Upstream `develop` pinned commit: `926bf4b5cfd979c951a933e75e615f54430e8d8a` (14 Oct 2026 UTC).
- The four Python 3.15.1 CLI golden-output failures are associated with new `os.path.commonprefix()` deprecation warnings; the earlier `codecs.open()` issue had already been fixed in `develop`.

## Patch

Apply `cpplint-python315-commonpath.patch` only to a clone or fork at the pinned upstream commit. It touches exactly three files:

- `cpplint.py`: change two repository-path prefix comparisons to `os.path.commonpath()`; change `_IsParentOrSame` to component-aware path ancestry with `ValueError` handling for different Windows drives.
- `cpplint_unittest.py`: add 5 test cases comprising path boundary, Git/Hg/SVN and legacy SVN repository-path checks.
- `CHANGELOG.rst`: add an unreleased compatibility entry.

Official Python path documentation: https://docs.python.org/3.15/library/os.path.html

## Reproducible verification

- Initial unfiltered Python 3.15.1 regression: https://github.com/Csq57/ai-python-repository-stabilization-case-study/actions/runs/40091341842
- Isolating the deprecation warning (diagnostic only): https://github.com/Csq57/ai-python-repository-stabilization-case-study/actions/runs/40091662602
- Functional patch CI: https://github.com/Csq57/ai-python-repository-stabilization-case-study/actions/runs/40160085885 — **9/9 success**, each with **236 passed**, covering Ubuntu/Windows/macOS × Python 3.13/3.14/3.15.1.
- Final quality CI: https://github.com/Csq57/ai-python-repository-stabilization-case-study/actions/runs/40160493672 — **9/9 success**, all **236 passed** per job. Ubuntu Python 3.14 met cpplint's 95% coverage gate at **96.67%**; Pylint, Mypy, and pre-commit (including Ruff check/format, Codespell, pyproject-fmt and zizmor) passed.

The CI checks out the pinned public source and temporarily applies the patch without publishing or modifying the upstream repository. Python version 3.15.1 is pinned exactly; Python 3.13 and 3.14 matrix entries use GitHub-hosted patch versions.

## Reviewer notes and limits

- This patch removes three deprecation-triggering calls and verifies path-component rather than character-prefix ancestry. The `ValueError` path is covered on Windows using paths on different drives.
- A passing independent CI run is **not** an upstream maintainer review, repository permission grant, merge, or release.
- The source is pinned. Rebase and revalidate against the current upstream `develop` head before any actual PR, especially if the repository has changed.
- Do not automatically post upstream comments, PRs, review approvals, or releases. Seek the account owner's explicit permission before submitting.

## Proposed upstream PR

**Title:** `fix: avoid deprecated os.path.commonprefix in path checks`

**Body sketch:** Resolves the Python 3.15.1 `os.path.commonprefix()` deprecation warning that contaminates CLI golden-output comparisons. Uses `commonpath()` to compare directory components and catches cross-drive `ValueError`. Adds path-boundary and Git/Hg/SVN regression tests and a changelog entry. Validated against pinned `develop` on Linux, Windows, macOS and Python 3.13/3.14/3.15.1, with 236/236 tests in each job; coverage 96.67%, Pylint, Mypy, and pre-commit green. AI assistance disclosed; this is a scoped compatibility change, not a new Python interpreter release claim.
