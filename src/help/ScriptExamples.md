---
title:  'Finding Current Scripting Examples'
---

If you are new to OpenVSP, the confusing part is often not finding scripts. It is knowing what kind of file you are looking at: a small example, an automated test, a Python example, or historical validation material. This page answers the questions that are easy to get wrong when first browsing `examples/scripts`.

## I Only Need One Working Example. Where Should I Start?

Start with the smallest script that demonstrates the operation you need. A short file is usually easier to learn from than one of the large test or validation drivers.

| Goal | Good first example |
|:-----|:-------------------|
| Basic geometry/API calls | `CreateEditGeom.vspscript` |
| Airfoil export | `AirfoilExport.vspscript`, `SingleAirfoilExport.vspscript` |
| Geometry/result utilities | `DegenGeom.vspscript`, `DumpResults.vspscript` |
| Analysis workflows | `CFDMesh.vspscript`, `FEAMesh.vspscript`, `ParasiteDragScriptTest.vspscript` |

For Python material, see `examples/scripts/python_scripts`. As with the AngelScript examples, check the specific file before assuming that an older script is the preferred current workflow.

For AngelScript language features and API access used by Advanced Links, see [Advanced Parameter Linking](AdvLink.md).

## Why Do So Many Files Start With `Test`?

Many `Test*.vspscript` files in `examples/scripts` are both examples and automated regression tests. They are wired into OpenVSP's CTest suite from `src/test/scripttest/CMakeLists.txt`, so they intentionally include pass/fail checks in addition to the API calls a user may want to learn.

That distinction matters when reading them:

- the API calls can still be useful examples;
- the surrounding checks are there for regression coverage, not because every user script needs them;
- a test file may be longer or more defensive than the smallest standalone example of the same workflow.

If you are adapting a test for your own script, copy the minimum workflow you need rather than the whole test harness. If you are modifying the repository test itself, keep its checks intact.

The API help examples are also generated into automated tests, so current API documentation is a useful reference when you want a small example tied closely to a specific function.

## How Should I Read the Different Kinds of Script Files?

| What you found | How to treat it |
|:---------------|:----------------|
| A small named `.vspscript` example | Usually the best first place to learn one workflow |
| A `Test*.vspscript` file | A working example plus regression-test checks |
| A file under `python_scripts` | A Python example; check whether that specific file is current before building around it |
| `Master_VSP_VV_Script.vspscript` or its Python port | Historical VSPAERO V&V reference material, not the place to start new V&V development |

This is the main distinction to make before copying code. Two files can both run successfully and still have very different purposes.

## What About the Master VSPAERO V&V Scripts?

`Master_VSP_VV_Script.vspscript` is legacy material. A later Python port exists at `examples/scripts/python_scripts/Master_VSP_VV_script_test.py`, but that Python V&V collection is also not the maintained direction for new V&V development.

Both can still be useful for learning from historical studies and existing comparison logic. Do not treat either master script as the default place to add a new validation case. If you are planning new VSPAERO verification or validation work, check current project guidance or ask the maintainers where that work belongs.

## How Can I Tell Whether an Example Is Current?

Before building new work around an example that looks old, unusually large, or inconsistent with another file:

- compare it with the current `main` branch;
- check whether it is referenced by the current test suite;
- look for a smaller or newer Python or AngelScript example that demonstrates the same operation;
- prefer current API documentation and actively tested examples when they cover the same behavior.

A useful rule is to ask what role the file serves before asking whether it still runs. A historical example may still execute, but that does not make it the recommended starting point for new work.

## What If Two Examples Disagree?

Do not silently pick the more convenient one. First check current API documentation and actively tested examples. If the mismatch still appears real, report the specific files or instructions that disagree. A focused documentation mismatch is usually more useful to maintainers than expanding an older workflow that may already be superseded.
