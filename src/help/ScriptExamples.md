---
title:  'Finding Current Scripting Examples'
---

OpenVSP ships several kinds of scripting material. They are useful for different purposes, and not every script should be treated as a current tutorial or as a place to add new work. This page is a short map for users who are trying to find a good example without accidentally following a legacy workflow.

## Where to Start

For AngelScript, start in `examples/scripts`. Choose the smallest script that demonstrates the API or analysis workflow you need, then read it from top to bottom before copying pieces into your own script.

Useful examples include:

| Goal | Example |
|:-----|:--------|
| Basic geometry/API calls | `CreateEditGeom.vspscript` |
| Airfoil export | `AirfoilExport.vspscript`, `SingleAirfoilExport.vspscript` |
| Geometry/result utilities | `DegenGeom.vspscript`, `DumpResults.vspscript` |
| Analysis workflows | `CFDMesh.vspscript`, `FEAMesh.vspscript`, `ParasiteDragScriptTest.vspscript` |

For Python material, see `examples/scripts/python_scripts`, but check the file and nearby README before treating an older script as the preferred workflow.

For AngelScript language features and API access used by Advanced Links, see [Advanced Parameter Linking](AdvLink.md).

## Examples That Are Also Tests

Many files named `Test*.vspscript` in `examples/scripts` are executable regression tests as well as examples. They are wired into OpenVSP's CTest suite from `src/test/scripttest/CMakeLists.txt` and intentionally contain checks that return failures when behavior changes.

That makes them valuable because they show API calls that are exercised automatically, but it also means they may be more verbose than a clean tutorial. When adapting one:

1. identify the API calls that demonstrate the workflow you need;
2. keep the test checks intact if you are modifying the repository test itself;
3. if you only need a standalone user script, copy the minimum workflow rather than the whole test harness.

The API help examples are also generated into automated tests, so current API documentation is a useful reference when you want a small example tied closely to a specific function.

## Legacy VSPAERO V&V Material

The older `Master_VSP_VV_Script.vspscript` is legacy material. A later Python port exists at `examples/scripts/python_scripts/Master_VSP_VV_script_test.py`, but that Python V&V collection is also not the current maintained direction for new V&V development.

Both can still be useful for understanding historical studies and existing comparison logic. However, do not treat either master script as the default place to add a new validation case. If you are planning new VSPAERO verification or validation work, first check current project guidance or ask the maintainers where that work belongs.

## When an Example Looks Stale

Before building new work around an example that appears old or unusually complex:

- compare it with the current `main` branch;
- look for a newer Python or AngelScript equivalent nearby;
- check whether the example is referenced by the current test suite;
- prefer current API documentation and actively tested examples when they cover the same behavior.

If two examples disagree, or a documentation page points to a workflow that has been superseded, reporting that specific mismatch is usually more useful than expanding the old workflow.
