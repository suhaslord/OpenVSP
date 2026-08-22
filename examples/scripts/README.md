# OpenVSP scripting examples

This directory contains several different kinds of material: small AngelScript examples, regression tests that also serve as examples, Python examples, and historical verification/validation scripts.

## New here?

Start with the smallest file that matches the task you want to automate:

- `CreateEditGeom.vspscript` — create and modify geometry
- `AirfoilExport.vspscript` / `SingleAirfoilExport.vspscript` — export airfoils
- `DegenGeom.vspscript` — degenerate geometry
- `DumpResults.vspscript` — inspect results
- `CFDMesh.vspscript` — CFD mesh workflow
- `FEAMesh.vspscript` — FEA mesh workflow

Files beginning with `Test` often include regression assertions in addition to useful API examples. Copy the workflow you need rather than the entire test harness unless you are editing the test itself.

Python examples live in `python_scripts/`.

## Verification and validation

`Master_VSP_VV_Script.vspscript` and its Python port are historical VSPAERO V&V references. They are useful for understanding older studies, but they are not the default location for new validation work.

For new work, prefer one focused reproducible case with explicit inputs, one reference source, and a small set of comparison outputs. The in-program Help pages **Scripting Examples: Where to Start** and **Building a Reproducible Validation Case** describe that workflow in more detail.
