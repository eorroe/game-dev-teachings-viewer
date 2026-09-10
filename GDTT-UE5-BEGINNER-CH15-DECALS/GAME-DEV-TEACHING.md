# GDTT-UE5-BEGINNER-CH15-DECALS

## Overview

Learn to use UE5 Decals to add ground markings, dirt, and detail to surfaces using Quixel Bridge assets, with proper placement, orientation, and the Receive Decals toggle to control which objects receive decal projections. Decals are transparent 2D texture planes that project onto existing materials, dramatically improving scene detail with minimal performance cost.

## When to Follow Game Dev Teachings

- When you need to add surface details like road lines, blood splatter, or dirt to existing geometry
- When working with Quixel Bridge assets to enhance environment visuals
- When the user asks about projecting textures onto surfaces in UE5
- When specific meshes (characters, spaceships) should not receive decal projections

## Lessons From Game Dev Teachings

### Lesson 1

#### Examples

##### Example 1: Ground Markings with Road Line Decals

Example text

##### Example 2: Blood Splatter on Surfaces

Example text

#### Step 1: Source Decals from Quixel Bridge

Browse Quixel Bridge categories such as road lines, blood splatter, and concrete to find suitable decal assets. Import the desired decal textures into your UE5 project.

#### Step 2: Place Decals on Target Surfaces

Drag a decal from the Content Browser into the viewport and position it on the target surface. Ensure the blue projection arrow on the decal faces directly toward the surface so the texture projects correctly.

#### Step 3: Adjust Scale and Position

Scale the decal to fit the surface dimensions and reposition it as needed for visual design. Use the transform gizmo to refine placement.

#### Step 4: Create Variety Through Duplication and Rotation

Duplicate the decal and rotate copies to break repetition and add natural variation across the scene.

#### Step 5: Use Snapping Tools for Precise Placement

Enable snapping tools to align decals accurately to geometry edges, corners, or other reference points for clean, professional results.

#### Step 6: Organize Decals into Folders

Group related decals into folders within the Content Browser to keep the project organized and easy to navigate.

#### Step 7: Control Decal Reception with the Receive Decals Toggle

Select meshes that should not receive decals, such as characters or spaceships. In the Details panel, disable the Receive Decals toggle to prevent decal projections from appearing on those objects.

#### Step 8: Adjust Decal Size Per Axis

Fine-tune decal dimensions by adjusting size values on individual axes to achieve the best fit on non-uniform surfaces.

#### Best Practices

- ✅ Orient the blue projection arrow toward the target surface before finalizing placement
- ✅ Use snapping tools to maintain precise alignment with scene geometry
- ✅ Organize decals into folders for project cleanliness
- ✅ Duplicate and rotate decals to avoid obvious repetition
- ✅ Disable Receive Decals on characters and spaceships to preserve their appearance

#### Keep In Mind

- Decals are transparent 2D texture planes that project onto existing materials
- Decals have a minimal performance cost relative to their visual impact
- The before/after difference from adding decals can be dramatic

#### Security & Safety Notes

- Text

#### Common Pitfalls

- **Problem:** Decal texture appears distorted or invisible
  **Solution:** Verify the blue projection arrow is facing the target surface and that the surface material supports decal blending
- **Problem:** Decals appear on characters or spaceships when they should not
  **Solution:** Select the mesh and disable the Receive Decals toggle in the Details panel
- **Problem:** Decals look repetitive across the scene
  **Solution:** Duplicate decals, rotate them to different angles, and vary their scale slightly

## Glossary / Index

|Term|Definition|
|----|----------|
|Blue Projection Arrow|The directional indicator on a decal that shows which way the texture is projecting; must face the target surface|
|Content Browser|The UE5 panel used to browse, search, and manage project assets including decals|
|Decal|A transparent 2D texture plane that projects onto existing materials in UE5 to add surface detail|
|Details Panel|The UE5 panel that displays properties for selected objects, including the Receive Decals toggle|
|Quixel Bridge|A library of high-quality textures and assets that can be sourced for decal materials|
|Receive Decals Toggle|A setting in the Details panel that controls whether a specific mesh receives decal projections|
|Snapping Tools|Viewport aids that align objects to geometry edges, corners, or other reference points for precise placement|
