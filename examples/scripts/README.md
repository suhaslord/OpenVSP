# OpenVSP Example Scripts

This directory contains AngelScript examples for geometry creation, export, analysis workflows, result utilities, and automated regression coverage.

For a short guide to choosing a current example, understanding the `Test*.vspscript` files, and avoiding legacy VSPAERO V&V paths, see:

**Help → Finding Current Scripting Examples**

Source documentation: `src/help/ScriptExamples.md`

Useful starting points:

- `CreateEditGeom.vspscript` — basic geometry/API workflow
- `AirfoilExport.vspscript` — airfoil export
- `DegenGeom.vspscript` and `DumpResults.vspscript` — geometry/result utilities
- `CFDMesh.vspscript`, `FEAMesh.vspscript`, and `ParasiteDragScriptTest.vspscript` — analysis workflows
- `Test*.vspscript` — examples that also serve as automated tests; expect explicit pass/fail checks

VSPAERO note: `Master_VSP_VV_Script.vspscript` is legacy material. The Python port under `python_scripts` is newer, but is also not the preferred maintained path for new V&V development. Use those files for background unless a maintainer specifically directs new work there.
