# GDTT-UE5-BEGINNER-CH2-VIEWPORT: Viewport Navigation & Object Manipulation in Unreal Engine 5

## Overview

This teaching guides beginners through navigating the Unreal Engine 5 viewport and manipulating objects in a 3D scene. It covers camera controls, object placement via the Place Actors panel, transform gizmos for moving, rotating, and scaling, precise value entry in the Details panel, snapping tools, visibility toggles, and scene hierarchy management through the Outliner. By the end, you will have built a simple starter scene using fire and smoke particle effects, giving you hands-on experience with core level-design workflows.

## When to Follow Game Dev Teachings

- When you need to navigate the Unreal Engine 5 viewport efficiently during level design
- When placing and transforming objects in a scene using gizmos and precise values
- When organizing scene hierarchy with the Outliner and Details panels
- When the user asks about viewport controls, snapping, or particle setup in UE5

## Lessons From Game Dev Teachings

### Lesson 1: Viewport Navigation, Object Placement, and Basic Scene Assembly in Unreal Engine 5

#### Examples

##### Example 1: Navigating a Large Open Level

Use WASD + right-click free-cam movement to fly through the level, adjust speed with the slider or middle-mouse scroll, and press F to focus on specific objects while editing.

##### Example 2: Building a Starter Scene with Particles

Add fire and smoke particle systems from Starter Content, position them with gizmos, and organize their hierarchy in the Outliner.

#### Step 1: Navigate the Viewport Using Camera Controls

Hold right-click to enter free-cam mode. Use WASD to move horizontally, Q and E to move vertically. Move the mouse to look around. Adjust camera speed with the slider in the top-right corner or scroll the middle mouse wheel. Press F to focus the view on any selected object.

#### Step 2: Add Objects Using the Place Actors Panel

Open the Place Actors panel from the left sidebar or the top bar icon. Browse available actors and drag one into the viewport or double-click it to place at the default position.

#### Step 3: Move, Rotate, and Scale Objects Using Gizmos

Select an object in the viewport. Press W to activate the Move gizmo, E for Rotate, and R for Scale. Drag the colored axes to transform along the corresponding direction. Use the colored planes to transform along two axes at once.

#### Step 4: Enter Precise Transform Values in the Details Panel

With an object selected, open the Details panel on the right. Under the Transform section, manually enter Location, Rotation, and Scale values for exact placement and sizing.

#### Step 5: Use Snapping Tools for Accurate Placement

Enable snapping via the toolbar or Details panel to constrain movement, rotation, or scaling to grid increments or angular steps for precise alignment.

#### Step 6: Hide Objects with the H Key

Select an object and press H to toggle its visibility in the viewport. Press Shift+H to hide all unselected objects. This helps isolate individual elements while building a scene.

#### Step 7: Manage Scene Hierarchy with the Outliner

Use the Outliner panel to view all objects in the scene. Select, rename, reparent, or delete objects directly from the hierarchy list. Drag items to reorganize parent-child relationships.

#### Step 8: Build a Simple Scene Using Starter Content Particles

Open the Place Actors panel, find the Starter Content folder, and drag a fire and smoke particle system into the scene. Position them using Move, Rotate, and Scale gizmos. Adjust their values in the Details panel and confirm visibility in the Outliner.

#### Best Practices

- ✅ Hold right-click before using WASD to avoid accidental camera movement
- ✅ Use the F key to quickly refocus on objects after navigating
- ✅ Snapping should be enabled for alignment-sensitive tasks like wall placement
- ✅ Organize objects logically in the Outliner using clear naming conventions
- ✅ Use precise transform values for exact positioning rather than eyeballing
- ✅ Hide distracting objects with H to focus on a single area of the scene

#### Keep In Mind

- The F focus shortcut only works when an object is already selected in the viewport or Outliner
- Middle-mouse scroll adjusts camera speed only when in free-cam mode (right-click held)
- The Place Actors panel requires Starter Content to be enabled in your project settings

#### Security & Safety Notes

- No user-generated content or online assets are required for these core workflow exercises
- Always save your level regularly while building scenes to avoid losing progress
- Starter Content particles are local assets and do not require external downloads

#### Common Pitfalls

- **Problem:** Camera moves without wanting it to after releasing right-click
  **Solution:** Ensure you release right-click fully; holding it slightly activates free-cam mode again
- **Problem:** Objects cannot be placed because the grid blocks them
  **Solution:** Toggle grid snapping off temporarily or adjust the object's Location Z value
- **Problem:** Gizmo axes are confusing or do not respond
  **Solution:** Ensure the object is selected (check Outliner) and that no other tool (like selection) is overriding the transform mode

## Glossary / Index

|Term|Definition|
|----|----------|
|Camera Speed Slider|A viewport UI control that adjusts how fast the camera moves during free-cam navigation|
|Details Panel|A right-side panel that exposes all editable properties of the currently selected object|
|Fire Particle|A particle effect from Starter Content used to simulate fire in a scene|
|Free-Cam Movement|A viewport navigation mode activated by holding right-click, allowing full 6-DOF camera control|
|Gizmo|A visual 3D handle (Move, Rotate, Scale) attached to a selected object for direct manipulation|
|H Key|A shortcut that toggles visibility of the selected object in the viewport|
|Location Transform|The XYZ world-space position values of an object in the Details panel|
|Move Gizmo (W)|The transform mode that allows dragging an object along X, Y, and Z axes|
|Outliner|A panel listing all actors in the current level, used for selection and hierarchy management|
|Parent-Child Relationship|A hierarchy link where one object (child) is attached to and inherits transforms from another (parent)|
|Particles|Visual effects such as fire and smoke, typically using sprite-based systems|
|Place Actors Panel|A sidebar panel used to browse and drag actors into the level viewport|
|Rotation Transform|The XYZ rotational values (in degrees) of an object in the Details panel|
|Rotate Gizmo (E)|The transform mode that allows rotating an object around its axes|
|Scale Transform|The XYZ uniform or non-uniform scale values of an object in the Details panel|
|Scale Gizmo (R)|The transform mode that allows resizing an object along its axes|
|Scene Assembly|The process of placing, transforming, and organizing actors to build a complete level|
|Shift+H|A shortcut that hides all objects except the currently selected one in the viewport|
|Smoke Particle|A particle effect from Starter Content used to simulate smoke in a scene|
|Snapping|A feature that constrains transform operations to fixed increments (grid, rotation angles, scale)|
|Starter Content|A built-in collection of assets (meshes, materials, particles) available when creating new UE5 projects|
|Transform|The combined Location, Rotation, and Scale properties defining an actor's position and orientation|
|Viewport|The central 3D scene editor window where levels are built and previewed|
|WASD|Keyboard keys used for horizontal free-cam movement in the viewport|
