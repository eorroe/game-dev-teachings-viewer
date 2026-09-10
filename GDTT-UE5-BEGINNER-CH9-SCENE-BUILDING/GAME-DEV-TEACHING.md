# GDTT-UE5-BEGINNER-CH9-SCENE-BUILDING

## Overview

Learn to build a complete spaceship hangar scene with emissive pillar lights, LED strips, and wall details using UE5 modeling tools, material instances, Pattern duplication, and actor merging for optimized scene assembly. This chapter walks through creating light fixture geometry from primitives, wiring up real-time-controllable emissive materials, and populating pillars and columns with symmetrical lighting using the Pattern and Transform Mirror tools.

## When to Follow Game Dev Teachings

- When you need to add emissive pillar lights to a sci-fi spaceship hangar scene
- When working with UE5 modeling tools to create custom light fixture geometry
- When you need to duplicate and arrange objects symmetrically across a scene using Pattern and Mirror tools
- When the user asks about merging multiple meshes into a single optimized static mesh with multiple material slots

## Lessons From Game Dev Teachings

### Lesson 1: Creating Emissive Lights and the Spaceship LED Rim

#### Examples

##### Example 1: Building Pillar Light Fixtures

Creating a rounded rectangle light fixture with a metallic base, then setting up an emissive material with RGB color and intensity control.

##### Example 2: Pattern Duplication of Big Pillar Lights

Using the Pattern tool on the Modeling tab to create a linear array of 5 lights, rotating and positioning them along a pillar, then toggling between World and Local coordinate space for precise manipulation.

##### Example 3: Transform Mirror for Symmetrical Placement

Using Transform > Mirror to reflect a group of lights across the Z and Y axes to populate the opposite side of the scene without manual placement.

##### Example 4: Merging Multiple Lights Into a Single Mesh

Selecting 5 pillar light actors and using Actor > Merge Actors to combine them into one static mesh with multiple material slots, reducing draw calls and simplifying scene management.

##### Example 5: Creating the Spaceship LED Rim

Duplicating faces from the spaceship body, extruding them outward for depth, inserting an edge loop to separate metal from emissive, then using the Attributes > Edit Materials paintbrush to assign the emissive material to the outer strip.

#### Step 1: Create the Light Fixture Geometry

Open the Modeling tab. Place a Rectangle primitive in the scene and raise it off the floor. Change the rectangle type to Rounded and adjust the Width and Depth values to get the desired shape. Duplicate the rectangle with Alt, scale it up slightly with R, and position it directly underneath the first to serve as the base.

#### Step 2: Extrude for Depth

Enter selection mode, select the top rectangle face, then open PolyGroup Edit. Use the Extrude tool with the viewport set to Fixed. Enter a negative value (e.g., -15) to push the light face downward. Repeat the same extrude for the base rectangle. Accept the operation when the depth looks correct.

#### Step 3: Create the Emissive Light Material

In the Content drawer, create a new folder called "Emissive Lights" or "Light Materials." Inside, create a new material called "Light Emissive" and create a material instance from it. Open the material, add an RGB node for the emissive color, and connect it to the Emissive Color input. Add a Multiply node after the RGB to control intensity.

#### Step 4: Convert Values to Material Parameters

Right-click the RGB node and select "Promote to Parameter" to create a Color parameter called "Emissive Color." Right-click the input value of the Multiply node and promote it to a Scalar parameter called "Emissive Strength." Apply and save the material. Open the material instance to adjust color and intensity in real time.

#### Step 5: Apply Materials and Merge Actors

Apply the emissive material instance to the light faces and a metallic starter content material (e.g., Metal Steel) to the base faces. Select both the light and base actors, then go to Actor > Merge Actors. Name the resulting static mesh (e.g., "Small Light" or "Big Pillar Light") and save it into a dedicated folder such as "Big Pillar Lights." The merged mesh will have two material slots, one for each material applied before merging.

#### Step 6: Create a Pattern for Big Pillar Lights

With the merged light mesh selected, open the Modeling tab, go to XForm > Pattern. Set the pattern type to Line, change the axis to Y, adjust the Extent to control spacing, and set Count to the desired number of instances (e.g., 5 or 6). Rotate the pattern group 45 degrees, then use the Viewport gizmo to position the lights along the pillar. Use the World/Local toggle in the top-right of the viewport to switch coordinate space: use World for global positioning and Local to move along the object's own rotated axes.

#### Step 7: Mirror Lights Across the Scene

Select all lights on one side of the scene. Use Right Click > Transform > Mirror and experiment with the X, Y, and Z axes to find the correct reflection axis. Mirror across Z to flip to the ceiling or opposite pillar face, and mirror across Y to duplicate to the opposite side of the room. After mirroring, use Local space to pull the mirrored group into precise position.

#### Step 8: Build Small Pillar Lights

Create two additional rounded rectangle lights with different depths for the small pillars. Extrude each individually in PolyGroup Edit. Apply the same emissive and metallic materials. Select all five small pillar light actors (alternating small, big, big, small, small), merge them into a single "Small Pillar Lights" static mesh, and place them into the smaller pillars using Alt-drag and local rotation.

#### Step 9: Create the Spaceship LED Rim

Select the spaceship mesh and switch the viewport to Unlit mode for better visibility. In PolyGroup Edit (Faces mode), select the outer edge faces of the spaceship hull. Use Duplicate to copy the selected faces, pull them outward to create a gap, then use Extrude with a positive value to give the strip depth.

#### Step 10: Insert Edge Loop and Separate Material Regions

In PolyGroup Edit, use Insert Edge Loop to create a cut that divides the extruded strip into an outer metal band and an inner emissive band. Accept the edge loop, then select the inner faces that should become the light. Use Extrude with Selected Triangle Normals enabled, extruding inward (e.g., value 350) to create the recessed emissive area.

#### Step 11: Paint Material Slots on the LED Rim

Switch to the Attributes panel and open Edit Materials. The tool presents a paintbrush cursor. Reduce the brush Size in the tool settings, or open Advanced and set a precise Radius value. Paint over the inner faces that should be emissive. In the Materials dropdown at the bottom of the Attributes panel, click Add to add a new material slot, then select the "Light Emissive" instance material. Set that material as the Active Material, then click "Assign Active Material" to apply it to the painted faces. Accept the tool and switch back to Lit mode to see the result.

#### Step 12: Verify Global Material Control

Open the "Light Emissive" master material and adjust the Emissive Color (e.g., to red or blue) and Emissive Strength. All instances across the scene—including the big pillar lights, small pillar lights, and the spaceship LED rim—update in unison because they all share the same material instance.

#### Best Practices

- ✅ Apply all materials before merging actors so the merged mesh retains multiple material slots
- ✅ Toggle to Local coordinate space when moving or rotating objects along their own rotated axes
- ✅ Use the Pattern tool instead of manual Alt-drag when placing more than 3–4 repeated objects
- ✅ Keep emissive intensity values at or below 1 in the Multiply node to avoid over-brightening
- ✅ Use material instances rather than unique materials so all lights can be controlled from one place
- ✅ Insert an edge loop before painting material slots to isolate the regions that need different materials

#### Keep In Mind

- The Pattern tool is found under Modeling tab > XForm > Pattern, not as a standalone top-level tab entry
- Merge Actors requires the actors to be in the same content folder; the resulting static mesh inherits material slots from the source actors
- The Attributes > Edit Materials paintbrush defaults to a large radius; always reduce it in Advanced settings for fine control
- Promoting a node to a parameter can be done by right-clicking the node itself (for color) or right-clicking the value input (for scalars)
- The World/Local toggle is in the top-right of the UE5 viewport and affects all transform gizmos

#### Security & Safety Notes

- Always save materials before testing changes in the viewport to avoid losing work
- When duplicating faces from an existing mesh (e.g., the spaceship hull), verify face selection carefully to avoid accidentally modifying the source geometry
- Merge Actors is a destructive combination; hide or delete originals only after confirming the merged result is correct

#### Common Pitfalls

- **Problem:** Merged mesh has only one material slot
  **Solution:** Apply different materials to the source actors before merging; merging two actors with identical materials produces only one slot
- **Problem:** Entire extruded face becomes one emissive color instead of a rim strip
  **Solution:** Insert an edge loop to split the face into metal and emissive regions before painting material slots
- **Problem:** Pattern objects are misaligned or at the wrong angle
  **Solution:** Adjust the Pattern axis (X/Y/Z), fine-tune the Extent and Count values, and use snapping for precision
- **Problem:** Cannot pull object along its rotated axis
  **Solution:** Toggle the viewport gizmo from World to Local coordinate space
- **Problem:** Emissive material appears black or too dim
  **Solution:** Ensure the Multiply node input value is above 0 (e.g., 1) and that the material instance is applied to the correct material slot

## Glossary / Index

| Term | Definition |
|---|---|
| Actor Merge | The process of combining multiple scene actors into a single static mesh via Actor > Merge Actors, reducing draw calls and consolidating control |
| Attributes > Edit Materials | A modeling-mode paint tool in UE5 used to paint material IDs directly onto mesh faces for per-face material assignment |
| Coordinate Space (World vs. Local) | World space uses global scene axes for transforms; Local space uses the object's own rotated axes, enabling manipulation along an object's tilted orientation |
| Edge Loop Insertion | A PolyGroup Edit operation that adds a cut around a mesh face to create a new boundary, used to split a surface into regions for different materials |
| Emissive Material | A UE5 material that produces its own visible light via the Emissive Color input, used for glowing surfaces like LEDs and light fixtures |
| Extrude | A modeling operation that pushes or pulls selected faces along their surface normal to add depth or thickness to geometry |
| Material Instance | A lightweight derivative of a master material that exposes selected parameters (color, scalar) for per-instance real-time control without recompiling the shader |
| Material Parameter | A promoted shader input (Color or Scalar) exposed on a material instance, allowing artists to tweak values at runtime without opening the material editor |
| Merge Actors | UE5 editor command that bakes selected actors into one static mesh asset, inheriting material slots from the source actors |
| Modeling Tab | UE5 editor tab containing mesh editing tools including PolyGroup Edit, Extrude, Insert Edge Loop, Pattern, and XForm |
| Multiply Node | A material graph math node used to scale or combine values; used here to control emissive intensity by multiplying the RGB color by a scalar strength value |
| Pattern Tool | A Modeling tab > XForm tool that creates linear, grid, or circular arrays of selected geometry with controllable count and spacing |
| PolyGroup Edit | UE5's face-level mesh editing mode, used to select faces and apply operations like Extrude and Insert Edge Loop |
| RGB Node | A material graph node that defines a color via Red, Green, and Blue float inputs; the primary source for Emissive Color |
| Transform Mirror | A right-click transform operation that reflects selected actors across a chosen axis (X, Y, or Z), used for symmetrical scene population |
| Unlit Viewport Mode | A UE5 viewport shading mode that renders geometry without lighting, useful for visually inspecting face selection and emissive regions |
