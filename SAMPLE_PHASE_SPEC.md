# Fictional Sample Phase Specification

**Demonstration only.** The repository, file names and evidence below are
fictional. They are not copied from OpenTrendIQ Lite or a client repository.

## Repository

example-python-service

## Desired behaviour

Reject an uploaded record when its required identifier is missing or contains
only whitespace. Return the existing invalid-input result without writing a
partial output file.

## In scope

- src/example_service/parser.py
- tests/test_parser.py

## Non-goals

- No API redesign.
- No dependency changes.
- No database migration.
- No new command-line options.
- No formatting of unrelated files.
- No change to valid-record output.

## Protected behaviour

- The public parse_record function signature remains unchanged.
- Valid records keep the same output schema.
- Invalid input must not create or replace an output file.
- Existing exception types remain stable.

## Required checks

    python -m pytest tests/test_parser.py -q
    python -m pytest -q

## Acceptance conditions

- A new test reproduces the missing-identifier case before the fix.
- Empty and whitespace-only identifiers produce the documented invalid result.
- No output file is written for either invalid case.
- Existing valid-input tests still pass.
- The full suite passes or any unrelated baseline failure is documented.
- The diff contains only the two in-scope files.

## Rollback

The change is delivered on a separate branch or patch. If a protected contract
changes, the patch is not accepted and can be discarded without altering the
baseline.
