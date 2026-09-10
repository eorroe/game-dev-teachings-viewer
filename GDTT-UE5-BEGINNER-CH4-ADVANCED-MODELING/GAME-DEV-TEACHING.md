# Advanced Modeling Techniques for Spaceship Hangar Environments in Unreal Engine 5

## Overview

This game dev teaching teaches advanced modeling techniques in Unreal Engine 5 for creating detailed architectural structures such as a Star Wars-style spaceship hangar. It covers polygroup edit mode, selection filters, back face handling, edge loop insertion, face extrusion, and proper scaling to industry-relevant dimensions. The skills taught here are essential for building believable interior environments and structural geometry in real-time 3D scenes.

## When to Follow Game Dev Teachings

- When you need to model complex architectural or industrial structures in Unreal Engine 5
- When working with interior environment geometry that requires face, edge, and vertex-level precision
- When the user asks about creating structural elements like pillars, walls, or hangar bays
- When scaling 3D assets to realistic real-world proportions for cinematic or game scenes
- When learning to use polygroup edit mode to organize and edit mesh geometry efficiently

## Lessons From Game Dev Teachings

### Lesson 1: Polygroup Edit Mode and Selection Filters

#### Examples

##### Example 1: Organizing Complex Mesh Geometry

Use polygroup edit mode to group faces of a hangar structure so they can be selected, moved, or modified together as a unit rather than face-by-face.

##### Example 2: Precise Component Selection

Switch between faces, edges, and vertices selection filters to target exactly the geometry element you need when modeling structural components like pillar bases or ceiling beams.

#### Step 1: Enter Polygroup Edit Mode

Activate polygroup edit mode in the modeling tool. This mode allows you to assign and manage face groups on your mesh so that related faces can be selected as a single unit for faster editing.

#### Step 2: Assign Polygroups to Mesh Faces

Select the faces that make up a logical component (such as a hangar wall section or pillar base) and assign them to a dedicated polygroup. Repeat for each major structural section of the hangar.

#### Step 3: Use Faces Selection Filter

Switch to the faces selection filter mode. With this filter active, you can click to select individual faces or drag to marquee-select groups of faces. Use this when you need to extrude, move, or delete specific surface areas of the geometry.

#### Step 4: Use Edges Selection Filter

Switch to the edges selection filter mode. This mode highlights the edges of your mesh and allows you to select edge loops or individual edges. Use this when adding detail lines, inserting edge loops, or modifying the outline of a structure.

#### Step 5: Use Vertices Selection Filter

Switch to the vertices selection filter mode. This mode shows the corner points of your mesh geometry. Use this for fine vertex-level adjustments when rounding corners or repositioning structural attachment points.

#### Step 6: Disable "Hit Back Faces"

Locate the "hit back faces" option in your modeling tool settings and disable it. This prevents accidentally selecting geometry on the opposite (interior or hidden) side of your mesh when clicking through thin walls or enclosed structures. This is especially important when modeling enclosed spaces like a hangar where front and back faces are close together.

#### Best Practices

- ✅ Use polygroup edit mode to organize large meshes into manageable sections before detailed editing
- ✅ Switch selection filters deliberately based on the edit task: faces for surfaces, edges for topology, vertices for pin-point placement
- ✅ Disable "hit back faces" when working on enclosed or double-sided geometry to avoid unintended selections
- ✅ Assign polygroups early in the modeling process to save time during later refinement passes

#### Keep In Mind

- Polygroups are a visual and selection aid only; they do not change the underlying mesh topology or geometry by themselves
- Selection filter modes are mutually exclusive; switching to one mode deselects elements selected under a different mode
- "Hit back faces" is a helpful toggle for transparent or thin geometry work, but should be disabled when precision front-face selection is required

#### Security & Safety Notes

- When exporting or sharing your modeled assets, ensure that all geometry is manifold (no non-manifold edges) to prevent rendering issues in Unreal Engine
- Always save your work before running operations like extrude or edge loop insertion, as undo history may be limited in some modeling tools

#### Common Pitfalls

- **Problem:** Selecting internal geometry when trying to edit the outer surface of an enclosed hangar structure
  **Solution:** Disable "hit back faces" and confirm your selection filter is set to faces before clicking on geometry
- **Problem:** Accidentally selecting too many faces after switching polygroups
  **Solution:** Deselect all before switching polygroups or selection modes to carry forward only your intended selection
- **Problem:** Edge loops inserted with uneven spacing causing distorted geometry
  **Solution:** Enable even spacing mode on the insert edge loops tool before running the operation

### Lesson 2: Insert Edge Loops and Face Extrusion

#### Examples

##### Example 1: Adding Structural Detail to Hangar Walls

Use the insert edge loops tool with even spacing enabled to add supporting geometry lines to hangar walls, enabling sharper bends, panel lines, or support beam grooves without distorting the overall shape.

##### Example 2: Creating Pillars via Face Extrusion

Extrude a flat face upward along the triangle normals direction with a fixed distance to build the vertical height of a hangar support pillar from a single base face.

#### Step 1: Select Target Edges for Insertion

Switch to edges selection mode and select the edge or edge loop where you want to insert a new loop of geometry. For adding detail to a straight wall, select the top or bottom edge loop of the wall face.

#### Step 2: Activate Insert Edge Loops Tool

Open the insert edge loops tool and enable even spacing. Even spacing ensures the new edge loop is inserted at a mathematically uniform distance from the selected edge, maintaining clean topology.

#### Step 3: Configure Insertion Parameters

Set the number of edge loops to insert (typically 1-2 for subtle detail, more for heavy subdivision) and confirm that even spacing is active. Preview the insertion before applying.

#### Step 4: Apply Insert Edge Loops

Execute the insert edge loops operation. The new edge loop(s) appear evenly distributed between the selected edges, subdividing the face into additional geometry segments.

#### Step 5: Select Faces to Extrude

Switch to faces selection mode and select the face or group of faces you want to extrude. For building a pillar, select the base face on the hangar floor where the pillar will originate.

#### Step 6: Activate Extrude Tool

Open the extrude tool and set the extrusion type to "fixed distance." Set the extrusion direction to follow the selected triangle normals direction so the geometry projects outward from the face's natural orientation.

#### Step 7: Set Extrusion Distance

Enter the desired extrusion distance (e.g., the height of the hangar pillar). Confirm the value and apply the extrusion. The selected face is projected along its normals to create the pillar body.

#### Step 8: Repeat for All Pillars

Repeat the face extrusion process for each pillar location around the hangar floor plan, maintaining consistent distance and direction for uniform pillar heights.

#### Best Practices

- ✅ Always enable even spacing when inserting edge loops to avoid stretched or compressed geometry
- ✅ Use fixed-distance extrusion rather than freehand extrusion for structural elements that require consistent dimensions
- ✅ Extrude along triangle normals direction to ensure geometry projects in the correct outward direction
- ✅ Insert edge loops before extruding faces when you need the extruded geometry to have its own clean topology

#### Keep In Mind

- Even spacing distributes edge loops proportionally; if the source edge is very long, even one loop may create a large face
- Fixed distance extrusion is measured in world units; verify your scene scale before extruding large structures
- Triangle normals direction determines which side of the face is considered "outward"; verify face orientation before extruding

#### Security & Safety Notes

- After extruding many faces, check for non-manifold geometry that could cause issues when importing into Unreal Engine
- Save incrementally when performing batch extrude operations across many pillar locations

#### Common Pitfalls

- **Problem:** Extruded faces go in the wrong direction because normals are flipped
  **Solution:** Confirm the triangle normals direction is set correctly, or flip normals on the source face before extruding
- **Problem:** Edge loops bunch up at one end of an edge after insertion
  **Solution:** Ensure even spacing is enabled; if the edge is uneven, consider subdividing it first for a cleaner insertion

### Lesson 3: Scaling Spaceship Assets to Real-World Proportions

#### Examples

##### Example 1: Positioning a Spaceship Inside a Hangar

Scale the spaceship model to approximately 180m in length and 30-40m in height so it fits proportionally and realistically inside the modeled hangar environment.

##### Example 2: Maintaining Cinematic Scale

Use known real-world reference dimensions (such as the length of a real aircraft carrier or large building) to guide the scale of both the hangar and the spaceship, ensuring the final scene reads believably in a cinematic render.

#### Step 1: Determine Target Dimensions

Establish the target real-world scale for the spaceship: approximately 180m length and 30-40m height. Record these as reference values for the modeling or scaling step.

#### Step 2: Measure Current Spaceship Scale

Select the spaceship mesh in Unreal Engine 5 and check its current bounding box dimensions in the World Outliner or Details panel. Note the current length and height in Unreal units.

#### Step 3: Calculate Scale Factor

Compute the ratio between the target dimension and the current dimension. For example, if the current spaceship length is 18 units and the target is 180m, the scale factor is 10x.

#### Step 4: Apply Uniform or Axis-Specific Scale

Apply the calculated scale factor to the spaceship actor. Use uniform scaling if the model needs to grow proportionally on all axes. Use axis-specific scaling if only one dimension (such as length) needs adjustment.

#### Step 5: Verify Fit Inside the Hangar

After scaling, place the spaceship inside the hangar environment and visually confirm that it fits with appropriate clearance on all sides. Adjust the scale factor if the ship is too large or too small relative to the hangar interior.

#### Step 6: Lock Final Scale

Once satisfied with the fit, lock or freeze the spaceship's transform scale to prevent accidental resizing during further scene editing.

#### Best Practices

- ✅ Use real-world reference dimensions as the basis for all environment and asset scaling
- ✅ Verify scale early and often by comparing multiple assets in the same scene
- ✅ Lock transforms on finalized scaled assets to prevent accidental modification
- ✅ Use Unreal Engine's unit system consistently (1 unit = 1cm by default) to keep scaling calculations accurate

#### Keep In Mind

- Unreal Engine 5 uses a default unit scale of 1 unit = 1 centimeter; a 180m spaceship would be 18,000 units long at default scale
- Realistic scale affects not only visual composition but also lighting, shadow, and post-processing results
- Overly large or small scale compared to the environment will break immersion in cinematic renders

#### Security & Safety Notes

- Scaling very large meshes (such as an 180m spaceship) can introduce floating-point precision issues in Unreal Engine; if rendering artifacts appear, consider splitting the model into sections or using World Origin Rebasing
- Always back up your scene before performing large-scale transforms on complex assets

#### Common Pitfalls

- **Problem:** Spaceship looks tiny or huge inside the hangar because the hangar and ship were modeled at different reference scales
  **Solution:** Establish a unified real-world reference scale before modeling any environment or asset; scale all elements against that single reference
- **Problem:** Scaling a skeletal mesh or blueprint instead of the static mesh causes animation or blueprint issues
  **Solution:** Scale the static mesh asset itself, or adjust the blueprint's default scale rather than scaling the placed actor in the level

## Glossary / Index

|Term|Definition|
|----|----------|
|Back Faces|The rear-facing polygons of a mesh surface; disabling "hit back faces" prevents these from being selected when clicking through thin geometry|
|Edge Loop|A continuous ring of edges that wraps around a mesh, used to add detail, control subdivision, or reinforce structural edges|
|Extrude|A modeling operation that projects a selected face or edge along a direction vector to create new geometry with depth or height|
|Fixed Distance|An extrusion mode where the face is projected by a specific numeric distance rather than freehand dragging, ensuring consistent dimensional output|
|Hit Back Faces|A selection setting that controls whether clicks can select geometry on the opposite side of a mesh; disabling it improves precision in enclosed models|
|Normals Direction|The perpendicular direction vector of a face surface; used in extrusion to determine which way new geometry projects|
|Polygroup Edit Mode|A ZBrush-style or modeling-tool mode that lets artists group mesh faces into named or colored sets for faster selection and editing|
|Selection Filter|A mode switch (faces, edges, vertices) that controls which type of geometry element can be selected in the modeling viewport|
|Triangle Normals|The outward-pointing vector perpendicular to a triangle face surface; determines the extrusion or shading direction of that face|
|Vertices|The corner points where edges meet on a mesh; selecting vertices allows pin-point repositioning of geometry|
