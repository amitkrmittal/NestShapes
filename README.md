# NestShape

**True-shape nesting plug-in for CorelDRAW 2021 to 2024.**

NestShape packs shapes by their real outlines, not by bounding boxes. Small parts drop into the pockets between larger parts, into concave curves, and into holes. It saves sheet material for laser cutting, plotter and vinyl cutting, signboards, acrylic, wood and metal sheet cutting, and similar jobs.

## Features

- True-shape nesting: parts are placed by outline, so small parts fill gaps and holes in larger ones.
- Rotation: step of 5, 10, 15, 30, 45 or 90 degrees, or none.
- Optional mirror (flip) and optional placement of parts inside holes of other parts.
- Minimum gap between parts, set in mm.
- Rectangular sheet of any size. More sheets are added side by side as needed, or limit them with Max sheets.
- Three quality levels: Faster, Medium, Optimized.
- Every placement is checked for overlap, and the result is verified again independently.
- Non-destructive: your originals are untouched. Nested copies are placed on red sheet outlines to the right of them, in a single Undo step.
- Live progress and a Cancel button. Cancelling adds nothing to the page.
- Report with placed / not placed count, sheets used, sheet coverage, packing density, time and overlap check.

## Requirements

- Windows, 64-bit.
- CorelDRAW Graphics Suite 2021, 2022, 2023 or 2024 (tested).
- Microsoft Visual C++ Redistributable 2015-2022 (x64). Most PCs already have it. If CorelDRAW does not load the plug-in, install it from Microsoft.

## Install

1. Download the ZIP from the Releases page and extract it. You get a folder named `NestShape`.
2. **Close CorelDRAW.**
3. Copy the whole `NestShape` folder into CorelDRAW's `Addons` folder:

   ```
   C:\Program Files\Corel\CorelDRAW Graphics Suite <year>\Programs64\Addons\
   ```

   Replace `<year>` with your version (2021, 2022, 2023 or 2024). The folder name can differ slightly between versions, so open `C:\Program Files\Corel` and look for it.

   The result should be:

   ```
   ...\Programs64\Addons\NestShape\NestShape.cpg
   ...\Programs64\Addons\NestShape\config.xml
   ...\Programs64\Addons\NestShape\Coreldrw.addon
   ...\Programs64\Addons\NestShape\NestShapeIcon.ico
   ...\Programs64\Addons\NestShape\NestShapeIcon.png
   ```

4. Windows will ask for administrator permission to copy into Program Files. Click Continue.
5. Start CorelDRAW. A **Nest shapes** button appears on the Standard toolbar.

If you cannot see the button, right-click the toolbar area, open Customization, and look for **Nest shapes** among the commands.

## Uninstall

Close CorelDRAW and delete the `NestShape` folder from the `Addons` folder.

## Use

1. Select the closed shapes to nest. If you imported an SVG, ungroup it first (Ctrl+U).
2. Click **Nest shapes** on the Standard toolbar.
3. Set the sheet size, gap and options, then click **Nest shapes** in the dialog.

| Setting | Meaning |
|---|---|
| Sheet width / height | Rectangular sheet in mm. |
| Gap | Minimum distance between parts, in mm. |
| Rotation step | 15 means try 0, 15, 30 ... 345 degrees. None keeps the original angle. |
| Nesting quality | Faster / Medium / Optimized. See below. |
| Flatten tolerance | Maximum error when curves are turned into polygons, in mm. |
| Max sheets | 0 = as many as needed. Otherwise parts that do not fit are reported as not placed. |
| Allow flipping | Also try mirrored parts. |
| Allow parts inside holes | Let small parts drop into holes of larger parts. |

### Nesting quality

Overlap is not possible at any setting.

- **Faster**: quickest. Can miss pockets that fit with almost no clearance.
- **Medium**: balanced. Finds tight pockets in most cases.
- **Optimized (best of 3 orders)**: tries three part orders and keeps the best result. About 3 times slower than Medium.

Start with Medium. Use Optimized for the final run and Faster for a quick look.

## Notes

- Your original objects are never changed. The plug-in duplicates each selected object and nests the duplicates.
- Text, rectangles and ellipses are converted to curves in the duplicate.
- A group is nested as one part.
- An object made of several separate pieces is treated as one outline around all its pieces, so nothing can overlap.
- Open curves (lines) are skipped and listed in the report.
- Dimensions are in millimetres.
- For many shapes, large sheets or small rotation steps, nesting can take time. Use **Cancel** to stop.

## Limitations

- Rectangular sheets only.
- Placement is greedy: the result is good but not guaranteed to be the best possible.
- Closed shapes only.

## Terms of use

This plug-in is provided free of charge, as is, without warranty of any kind. You use it at your own risk. Check the nested layout before cutting. Redistribution of the files or modification of the plug-in is not permitted without the author's written permission.

NestShape uses the Clipper2 library by Angus Johnson, under the Boost Software License 1.0.

## Support

Report problems via the Issues tab of this repository. Please include your CorelDRAW version, the sheet settings used, and, if possible, a small `.cdr` file that shows the problem.
