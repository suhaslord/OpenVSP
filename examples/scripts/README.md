# OpenVSP Example Scripts

This directory contains several different kinds of scripting material. If you are new to OpenVSP, the important first step is to tell whether you are looking at a small example, an automated test, a Python example, or historical validation material.

For a short guide organized around those new-user questions, see:

**Help → Finding Current Scripting Examples**

Source documentation: `src/help/ScriptExamples.md`

Good first examples:

- `CreateEditGeom.vspscript` — basic geometry/API workflow
- `AirfoilExport.vspscript` and `SingleAirfoilExport.vspscript` — airfoil export
- `DegenGeom.vspscript` and `DumpResults.vspscript` — geometry/result utilities
- `CFDMesh.vspscript`, `FEAMesh.vspscript`, and `ParasiteDragScriptTest.vspscript` — analysis workflows

A few distinctions that are easy to miss at first:

- `Test*.vspscript` files are examples that also serve as automated regression tests, so they include pass/fail checks that a normal standalone script may not need.
- `python_scripts` contains Python examples, but an older file should not automatically be treated as the preferred current workflow.
- `Master_VSP_VV_Script.vspscript` and its later Python port are historical VSPAERO V&V reference material. They are useful to learn from, but they are not the maintained place to start new V&V development.

When two examples disagree, prefer current API documentation and actively tested examples, then report the specific mismatch if it is still unclear.
