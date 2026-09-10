# GDTT-UE5-BEGINNER-CH12-IMPORTING-ASSETS

## Overview

Learn to import GLB and FBX 3D assets from Sketchfab into UE5, understand the four asset types produced by animated imports, bring in spacecraft with pre-baked animations, and use the Pattern tool with snapping and mirroring to populate scenes.

## When to Follow Game Dev Teachings

- When you need to import 3D models from Sketchfab into UE5
- When working with GLB or FBX asset formats and deciding which to use
- When the user asks about importing animated assets, static meshes, or duplicating objects in the scene

## Lessons From Game Dev Teachings

### Lesson 1

#### Examples

##### Example 1: GLB vs FBX Import from Sketchfab

GLB bundles textures automatically within the file, making it a convenient choice when importing animated models from Sketchfab. FBX separates geometry from textures, requiring manual material setup after import, but can be preferable for static meshes where tighter control over materials is desired.

##### Example 2: Lambda Shuttle with Pre-baked Animation

A Lambda-class shuttle imported as an animated GLB from Sketchfab produces four distinct asset types in UE5: a skeletal mesh for the model, an animation sequence for the pre-baked animation, a physics asset for collision, and a skeleton for rigging. The animation sequence can be applied directly to the skeletal mesh to drive movement.

#### Step 1: Import a 3D Asset from Sketchfab

Download the desired 3D model from Sketchfab. GLB files are recommended for animated models because they bundle textures automatically. FBX files are available for static models but require manual material assignment after import. In UE5, right-click in the Content Browser and choose Import. Select the file and confirm the import settings.

#### Step 2: Enable Combine Static Meshes

During import, enable the "Combine Static Meshes" option when importing GLB files. This prevents UE5 from generating thousands of separate parts for a single model, keeping the asset hierarchy manageable and improving performance.

#### Step 3: Identify the Four Animated GLB Asset Types

After importing an animated GLB, UE5 produces four asset types:
- **Skeletal Mesh** — the actual 3D model geometry
- **Animation Sequence** — the pre-baked animation data
- **Physics Asset** — collision bodies and constraints
- **Skeleton** — the bone hierarchy shared by mesh and animation

These assets appear as separate entries in the Content Browser and must be used together for the animation to function.

#### Step 4: Apply the Animation Sequence to the Skeletal Mesh

Drag the skeletal mesh into the level to place it. Then, from the Content Browser, drag the animation sequence asset onto the skeletal mesh in the scene. UE5 will automatically bind the animation sequence to the skeletal mesh and begin playing the pre-baked animation.

#### Step 5: Control Animation Playback via the Details Panel

Select the animated skeletal mesh in the scene. In the Details panel, locate the Animation section. Use the timeline slider to scrub through the animation sequence manually, or adjust playback settings such as looping behavior and play rate. This allows precise inspection and control of the animation without entering Sequencer.

#### Step 6: Switch Between Skeletal Mesh and Animation Sequence Workflows

UE5 supports both skeletal mesh imports with animation sequences and pure animation sequence workflows. If an asset was imported as a skeletal mesh but you need to swap animations, delete or replace the animation sequence asset associated with it. If you need to import purely as an animation, use the Animation Sequence import option in the Content Browser and re-parent it to the target skeleton.

#### Step 7: Import TIE Fighters as Static Meshes

For vehicles or props without animation, import FBX or GLB files as static meshes. After import, drag the static mesh into the scene. Static meshes do not require skeletons or animation sequences and are lighter on performance, making them ideal for repeated environment objects like TIE fighters.

#### Step 8: Use the Pattern Tool for Array Duplication

In the UE5 Modeling tab, select the Pattern tool to duplicate objects in a grid or radial array. Configure the number of instances along each axis, spacing between objects, and alignment. The Pattern tool is especially useful for quickly populating hangars, fleets, or formations with identical meshes.

#### Step 9: Apply Snapping and Mirroring for Precise Layout

Enable grid and rotation snapping in the UE5 viewport to ensure objects align cleanly to the scene grid. Use the mirror transform option to flip selected objects across an axis, which is helpful when placing opposing ships or symmetrical props. Combine snapping with reference images to match production designs accurately.

#### Best Practices

- ✅ Use GLB for animated imports from Sketchfab to preserve bundled textures
- ✅ Enable Combine Static Meshes during import to reduce asset count
- ✅ Verify all four animated GLB asset types are present before placing a model
- ✅ Use the Details panel timeline slider for quick animation previews
- ✅ Import non-animated spacecraft as static meshes for better performance
- ✅ Enable snapping when placing multiple identical objects
- ✅ Use reference images to guide scene layout and design accuracy

#### Keep In Mind

- GLB texture bundling means fewer import steps but less material customization compared to FBX
- FBX imports require manual material creation for each texture channel
- The Pattern tool operates on selected static meshes within the current level
- Snapping values can be adjusted in the UE5 editor settings for finer or coarser placement

#### Security & Safety Notes

- Only import assets from Sketchfab that you have the rights to use in your project
- Verify the license of downloaded 3D models before distributing a finished project
- Do not import untrusted or malware-embedded 3D files into a production UE5 project

#### Common Pitfalls

- **Problem:** Animation does not play after importing an animated GLB
  **Solution:** Ensure the animation sequence is dragged onto the skeletal mesh in the scene, not just opened in the Content Browser
- **Problem:** Thousands of separate parts appear in the Content Browser after import
  **Solution:** Re-import the GLB and enable Combine Static Meshes to consolidate the hierarchy
- **Problem:** Textures are missing after FBX import
  **Solution:** Manually create a material and assign the texture maps to the appropriate material slots
- **Problem:** Pattern tool duplicates objects in the wrong orientation
  **Solution:** Reset the object transform to world origin before running the Pattern tool, or adjust the pivot orientation

## Glossary / Index

|Term|Definition|
|----|----------|
|Animation Sequence|A UE5 asset containing pre-baked animation data that can be played on a skeletal mesh|
|Combine Static Meshes|An import option in UE5 that merges multiple imported parts into a single static mesh asset to reduce part count|
|FBX|A 3D file format that separates geometry from textures, commonly used for static mesh imports and requiring manual material setup|
|GLB|A binary 3D file format that bundles geometry and textures together, preferred for animated imports from Sketchfab|
|Lambda Shuttle|A spacecraft model used in the chapter as an example of importing an animated GLB with a pre-baked animation|
|Modeling Tab|The UE5 editor tab containing tools for editing and duplicating geometry, including the Pattern tool|
|Pattern Tool|A Modeling tab tool that duplicates selected objects in configurable grid or radial arrays for rapid scene population|
|Physics Asset|A UE5 asset containing collision bodies and physical constraints generated alongside skeletal mesh imports|
|Reference Images|2D images placed in the level viewport to guide scene layout and ensure design accuracy|
|Skeletal Mesh|The 3D model geometry asset produced by an animated GLB import, driven by an animation sequence and skeleton|
|Skeleton|The bone hierarchy asset shared between a skeletal mesh and its animation sequences|
|Sketchfab|An online platform for browsing, downloading, and sharing 3D models, including GLB and FBX files suitable for UE5|
|Snapping|A UE5 viewport feature that constrains object movement, rotation, and scale to defined increments for precise placement|
|Static Mesh|A UE5 asset type used for non-animated 3D objects, offering better performance for repeated environment props like TIE fighters|
|TIE Fighter|A spacecraft model used in the chapter as an example of importing a static mesh from Sketchfab|
