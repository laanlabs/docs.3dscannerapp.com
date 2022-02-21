---
createdAt: 2021-12-28T00:05:42.370Z
title: How To Export Scans into SketchUp
---

### Options for Exporting 3D Scans into SketchUp

[SketchUp](https://www.sketchup.com/) can import 3D Scans a couple of different ways. In general complex 3D Meshes or Point Clouds need a good graphics card to render well.

#### DAE Import
SketchUp natively support importing [DAE files](https://help.sketchup.com/en/sketchup/importing-and-exporting-collada-files#:~:text=Importing%20a%20COLLADA%20file,-To%20import%20a&text=Select%20File%20%3E%20Import.,list%20in%20the%20lower%20right.). Export your 3D Scans as DAE from the share menu and you can import into SketchUp. NOTE: Large and complex scans do not render well as DAE and it may be necessary to try one of the alternative methods

#### Point Cloud Import with SketchUp’s Scan Essentials
An add-on for new versions of SketchUp, [Scan Essentials ](https://blog.sketchup.com/article/turn-point-clouds-into-3d-models-with-scan-essentials)supports the importing of  PLY, E57, LAZ, and LAS point clouds. Download and install the [Extension](https://extensions.sketchup.com/extension/e51d2e99-5dae-4541-9d39-c3eb3a7d729b/trimble-scan-essentials-for-sketch-up) and then export your 3D Scan as one of the compatible point cloud formats.

#### 3rd Party Extensions
Sketchup has a number of extensions to aid with importing 3D Model files. Search the extension store for options, but two known working ones are:
* [Simlab Obj Importer](https://www.simlab-soft.com/3d-plugins/OBJ_Importer_For_Sketchup-main.aspx?locale=en)
* [Fluid Importer](https://www.fluidinteractive.com/products/sketchup-extensions/fluidimporter/)

#### transmutr (Paid Application with 7-day trial)
[Download transmutr](https://lindale.io/transmutr)
Export from 3DScanner App as OBJ and use the following settings:
* SCALE MULTIPLIER: 10000
* UP AXIS: +Y
