# Dated Engineering Evidence

## Evidence boundary

These results describe repository verification, not investment performance,
customer outcomes or future reliability. They were reproduced on
18 July 2026 from a clean local checkout based on the then-current master
baseline.

## Repository facts

- Package version: 1.0.0
- Declared Python support: 3.11 or later
- Project state: stable maintenance release
- Automatic trading: excluded
- Broker connection: excluded
- Account access: excluded
- Financial advice: excluded

## Full test suite

Command:

    uv run pytest -q

Result:

    693 passed, 2 skipped, 1 warning in 14.18s

The two skips came from Windows symlink support being unavailable. The warning
was a Starlette dependency deprecation warning related to the test client.

## Package build

Command:

    uv build

Result:

- opentrendiq_lite-1.0.0-py3-none-any.whl built successfully
- opentrendiq_lite-1.0.0.tar.gz built successfully

## Clean-wheel smoke test

The wheel was installed into a new Python 3.11.15 virtual environment using
no dependency resolution and no package index. Both entry paths succeeded:

    python -m opentrendiq_lite --help
    opentrendiq --help

This check confirms that the packaged module and console entry point can start
outside the development checkout. It is not a full runtime or provider test.

## Continuous integration

The configured GitHub Actions matrix includes:

- Ubuntu with Python 3.11 and 3.12;
- Windows with Python 3.11 and 3.12;
- optional-extras verification on Ubuntu with Python 3.11; and
- package build and clean-wheel jobs.

The latest master workflow run checked during preparation completed
successfully. The preceding four master workflow runs also completed
successfully.

## Refresh rule

Test counts, warnings, artefact names and CI state can change. Re-run all
commands and update this file before using the numbers after a product change.
