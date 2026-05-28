# Module Model Conversion (Short)

Recommended pipeline for probe module meshes:

1. Model in Fusion 360.
2. Export from Fusion to `USDZ`.
3. Import `USDZ` into Blender.
4. In Blender:
   - imported meshes often come parented to an empty transform node from CAD,
   - select the mesh and press `Alt + P → Clear Parent → Keep Transform`,
   - delete the point of parent which is out of model,
   - manually move the mesh to the world origin `(0,0,0)`,
   - set correct pivot: `Object → Set Origin → Origin to Geometry`,
   - rotate the module if necessary so that the **wide side of the module faces the Y axis (not X)**,
   - use `blank_panel_6u.glb` as the orientation reference,
   - the **positive Y direction (the side farther from the origin)** should represent the **top of the module**,
   - apply transforms (`Ctrl+A`: Rotation + Scale),
   - verify normals are correct,
   - keep real-world dimensions.
5. Export from Blender to `GLB` (`glTF 2.0 Binary`).
6. Put `.glb` into this folder and reimport in Godot.

Notes:
- Game preview uses bus/layer conventions, not CAD-accurate assembly constraints.
- For custom models, source materials from imported GLB are preserved.