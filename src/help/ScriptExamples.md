---
title:  'Scripting Examples: Where to Start'
---

OpenVSP ships with several kinds of examples. They are all useful, but they are not interchangeable. A new user can save a lot of time by first deciding whether a file is a small example, a regression test, a Python example, or historical verification and validation material.

## Start with the Smallest Example That Matches Your Goal

| Goal | Suggested first file |
|:-----|:---------------------|
| Create and edit geometry | `examples/scripts/CreateEditGeom.vspscript` |
| Export airfoils | `examples/scripts/AirfoilExport.vspscript` or `SingleAirfoilExport.vspscript` |
| Generate degenerate geometry | `examples/scripts/DegenGeom.vspscript` |
| Inspect analysis results | `examples/scripts/DumpResults.vspscript` |
| Build a CFD mesh workflow | `examples/scripts/CFDMesh.vspscript` |
| Build an FEA mesh workflow | `examples/scripts/FEAMesh.vspscript` |
| Run parasite-drag analysis | `examples/scripts/ParasiteDragScriptTest.vspscript` |

For Python examples, use `examples/scripts/python_scripts` and the generated Python API examples. Prefer a small, actively tested example over a large historical driver when both cover the same API.

## Why Are Many Examples Named `Test...`?

Many files under `examples/scripts` now serve two purposes:

1. they show how an API workflow is used; and
2. they run as regression tests and contain checks that can fail automatically.

That second job explains code that can look unnecessary in a user script: expected-value checks, error-count checks, cleanup code, and test-only setup. When learning from one of these files, copy the minimum workflow you need. When editing the repository test itself, keep the checks intact.

A useful rule is:

> **Example code teaches the workflow; test code proves the workflow still behaves as expected.**

## File Types You Will Encounter

| File type | What it is for | Good starting point? |
|:----------|:---------------|:---------------------|
| Small named `.vspscript` | One focused AngelScript workflow | Yes |
| `Test*.vspscript` | Working example plus regression assertions | Yes, after you identify the test-only parts |
| `python_scripts/*.py` | Python API examples and utilities | Yes for Python users |
| Generated API examples | Small examples tied to individual API calls and exercised by tests | Excellent for one API call |
| `Master_VSP_VV_Script.vspscript` | Historical VSPAERO V&V driver | No for new work |

## The Master VSPAERO V&V Scripts Are Historical References

`Master_VSP_VV_Script.vspscript` and its later Python port contain useful historical studies and comparison logic. They should not be treated as the default place to add a new verification or validation case.

For new work, start with the current solver/API path you actually want to test, reduce it to one reproducible case, and follow [Building a Reproducible Validation Case](ValidationWorkflow.md).

## How to Tell Whether an Example Is Current

Before basing new work on an example that looks old, unusually large, or inconsistent with another file:

- check whether it is referenced by the current test suite;
- compare its API calls with current generated API documentation;
- look for a smaller example that covers the same operation;
- check recent changes to the example when behavior is surprising;
- prefer a current tested example over a historical driver when both exist.

A file can still run and still be the wrong template for new development. The important question is not only **“does this execute?”** but also **“what role does this file serve today?”**

## A Good First Script

For a first repository-based experiment, keep the script intentionally small:

1. clear or create a model;
2. create only the geometry required by the example;
3. set the few parameters that matter to the behavior being demonstrated;
4. run one analysis or export operation;
5. inspect one or two results;
6. add an assertion only if the file is intended to become a regression test.

This structure is easier to debug than starting from a large all-in-one script.

## When Two Examples Disagree

Do not silently choose whichever one produces the expected result. First determine whether the files serve different purposes or use different solver/configuration assumptions. Check the current API documentation and the actively tested example path.

If the mismatch remains, report the exact two files, the OpenVSP version or commit, and the smallest behavior that differs. That gives maintainers something reproducible to investigate.

## Before Turning an Example into a Validation Case

A working example only proves that the workflow executes. A validation case needs a reference, controlled inputs, a comparison metric, and enough metadata for someone else to reproduce the result.

See [Building a Reproducible Validation Case](ValidationWorkflow.md) for a practical checklist.
