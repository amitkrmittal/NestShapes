# NestShape

**True-shape nesting macro for CorelDRAW (64-bit).**

NestShape packs shapes by their real outlines, not by bounding boxes. Small parts drop into the pockets between larger parts, into concave curves and into holes. It saves sheet material for laser cutting, plotter and vinyl cutting, signboards, acrylic, wood and metal sheet cutting, and similar jobs.

It installs as a GMS macro plus one DLL, so it works with any 64-bit CorelDRAW that has VBA, and it does not depend on a particular CorelDRAW version.

## Features

- True-shape nesting: parts are placed by outline, so small parts fill gaps and holes in larger ones.
- Rotation: step of 5, 10, 15, 30, 45 or 90 degrees, or none.
- Optional mirror (flip) and optional placement of parts inside holes of other parts.
- Minimum gap between parts, set in mm.
- Rectangular sheet of any size. More sheets are added side by side as needed, or limit them with Max sheets.
- Every placement is checked for overlap, and the result is verified again independently.
- Non-destructive: your originals are untouched. Nested copies are placed on red sheet outlines to the right of them, in a single Undo step.
- Progress window with a Cancel button. Cancelling adds nothing to the page.
- Report with placed / not placed count, sheets used, sheet coverage, packing density, time and overlap check.

## Requirements

- Windows 10 or 11, 64-bit.
- 64-bit CorelDRAW with VBA installed (VBA is an optional component in some versions; check Tools > Macros).

## What is in the download

| File | Purpose |
|---|---|
| `NestShapes.gms` | The macro. |
| `nestcore.dll` | The nesting engine and dialogs. Must sit in the same folder as the GMS file. |

## Install

1. **Close CorelDRAW.**
2. Open the GMS folder. Press Win+R, paste the path below, replace `<version>` with your version, and press Enter:

   ```
   %APPDATA%\Corel\CorelDRAW Graphics Suite <version>\Draw\GMS
   ```

   The folder name can differ slightly between versions. If this folder does not exist, look inside `%APPDATA%\Corel` for the `GMS` folder that already holds your other macros.
3. Copy **both** `NestShapes.gms` and `nestcore.dll` into that folder.
4. Start CorelDRAW.

If Windows marked the downloaded files as blocked, right-click each file, choose Properties, tick **Unblock** if shown, and click OK. Do this before step 3.

### Add a toolbar button (optional)

Tools > Customization > Commands > choose **Macros** in the list, find `NestShapeMod.NestShape`, and drag it onto a toolbar.

## Use

1. Select the closed shapes to nest. If you imported an SVG, ungroup it first (Ctrl+U).
2. Run the macro: Tools > Macros > Macro Manager > `NestShapeMod.NestShape`, or click your toolbar button.
3. Set the sheet size and options, then click **Nest shapes**.

| Setting | Meaning |
|---|---|
| Sheet width / height | Rectangular sheet in mm. |
| Gap between parts | Minimum distance between parts, in mm. |
| Rotation step | 15 means try 0, 15, 30 ... 345 degrees. None keeps the original angle. |
| Curve flatten tolerance | Maximum error when curves are turned into polygons, in mm. Smaller is more exact but slower. |
| Max sheets | 0 = as many as needed. Otherwise parts that do not fit are reported as not placed. |
| Allow flipping | Also try mirrored parts. |
| Allow parts inside holes | Let small parts drop into holes of larger parts. |

The result appears to the right of your original objects. Press Ctrl+Z once to undo the whole run.

## Notes

- Your original objects are never changed. The macro duplicates each selected object and nests the duplicates.
- Text, rectangles and ellipses are converted to curves in the duplicate.
- A group is nested as one part.
- An object made of several separate pieces is treated as one outline around all its pieces, so nothing can overlap.
- Open curves (lines) are skipped and listed in the report.
- Dimensions are in millimetres.
- With many shapes, large sheets or small rotation steps, nesting can take time. Use **Cancel** to stop.
- Selected objects named "NestShape sheet ..." (the red sheet outlines from an earlier run) are ignored.

## Troubleshooting

| Problem | What to try |
|---|---|
| "nestcore.dll was not found" | Copy `nestcore.dll` into the same folder as `NestShapes.gms`. The message lists every folder the macro searched. |
| "Windows could not load nestcore.dll" | CorelDRAW must be 64-bit. Unblock the file (see Install). Restart CorelDRAW after replacing the DLL, because Windows keeps it locked while CorelDRAW runs. |
| Macro does not appear in Macro Manager | Check that the GMS file is in the folder your CorelDRAW version uses, and that VBA is installed. |
| Some objects are skipped | Bitmaps and open curves cannot be nested. The report lists what was skipped and why. |

## Limitations

- Rectangular sheets only.
- Placement is greedy and uses the fast search: the result is good but not guaranteed to be the best possible, and very tight pockets can be missed.
- Closed shapes only.

## Terms of use

This macro is provided free of charge, as is, without warranty of any kind. You use it at your own risk. Check the nested layout before cutting. Redistribution of the files or modification of the macro is not permitted without the author's written permission.

NestShape uses the Clipper2 library by Angus Johnson, under the Boost Software License 1.0.

## Support

Report problems via the Issues tab of this repository. Please include your CorelDRAW version, the sheet settings used, and, if possible, a small `.cdr` file that shows the problem.
