# GDTT-UE5-BEGINNER-CH14-CLONING-CHARACTERS

## Overview

Learn to convert skeletal meshes to static meshes, create army formations with the Pattern tool, attach props to characters using Static Mesh components, add variation with Jitter, enable Nanite for high-polygon performance, and fix Nanite shadow artifacts with a console variable command.

## When to Follow Game Dev Teachings

- When you need to convert skeletal mesh characters into static meshes so they can be patterned and instanced
- When working with UE5 to create army formations or crowd scenes with repeated characters
- When you need to attach props like blasters or weapons to characters as Static Mesh components
- When the user asks about adding organic variation to instanced meshes using Jitter settings
- When you need to enable Nanite on static meshes to handle high-polygon assets without performance loss
- When Nanite shadow artifacts appear and you need to fix them using a console variable

## Lessons From Game Dev Teachings

### Lesson 1: Converting Skeletal Meshes to Static Meshes and Attaching Props

#### Examples

##### Example 1: Converting a Skeletal Mesh Character to a Static Mesh

Use the "Make Static Mesh" button in UE5 to convert a skeletal mesh character into a static mesh so it can be patterned and treated like any other geometry.

##### Example 2: Creating Static Mesh Permutations from Animation Frames

Duplicate the original skeletal mesh character and create multiple static mesh variations by baking different animation frames into static mesh snapshots, giving the army visual variety without animation overhead.

##### Example 3: Downloading a Blaster Prop from Sketchfab as GLB

Search Sketchfab for a blaster or prop model, download it as a GLB file, and import it into UE5 using the Combine Static Meshes option so it arrives as a clean single static mesh.

##### Example 4: Adding a Blaster as a Static Mesh Component to a Character Actor

In the UE5 Blueprint or actor hierarchy, add a Static Mesh component to a character actor, assign the blaster static mesh to it, and use transform copy/paste to position the blaster in the character's hand.

##### Example 5: Copying Transforms to Attach Props to Multiple Characters

Copy the location, rotation, and scale values from the first character's blaster component and paste them onto other character actors so every character holds the prop in the same position without manual adjustment.

#### Step 1: Convert a Skeletal Mesh Character to a Static Mesh

In the UE5 Content Browser, select the skeletal mesh character asset. Right-click it and choose "Make Static Mesh." Name the output static mesh (e.g., "Soldier_Static") and save it into a dedicated folder such as "Characters/Static."

#### Step 2: Create Multiple Static Mesh Permutations from Animation Frames

Open the skeletal mesh in the Persona editor or viewport. Scrub through the animation timeline to find visually distinct frames. At each desired frame, select the skeletal mesh, use Make Static Mesh again, and save each snapshot as a new static mesh variant (e.g., "Soldier_Pose_A", "Soldier_Pose_B"). These static mesh permutations will be used later in the Pattern tool to break up visual repetition.

#### Step 3: Download a Blaster Prop from Sketchfab

Go to Sketchfab and search for a blaster or weapon model suitable for the scene. Filter for downloadable models and choose the GLB format. During download, enable the "Combine Static Meshes" option so the model imports into UE5 as a single static mesh rather than a scattered group of parts.

#### Step 4: Import the Blaster into UE5

Drag the downloaded GLB file into the UE5 Content Browser. Confirm the import settings, making sure the static mesh import options are enabled. Save the imported blaster static mesh into a "Props" or "Weapons" folder.

#### Step 5: Add the Blaster as a Static Mesh Component

Open the character Blueprint or select the character actor in the level. In the Components panel, add a new Static Mesh component. Rename it "Blaster" or "Weapon." With the component selected, assign the imported blaster static mesh in the Details panel.

#### Step 6: Position the Blaster Using Transform Copy/Paste

Select the character actor, use the viewport gizmo to position and rotate the blaster static mesh component so it sits naturally in the character's hand. Once the position looks correct, select the Static Mesh component, open the Transform panel, right-click the Location, Rotation, and Scale fields, and choose Copy. Select the next character actor's Static Mesh component, right-click the same fields, and choose Paste to instantly match the transform.

#### Best Practices

- ✅ Convert skeletal meshes to static meshes before patterning so the Pattern tool treats them as geometry rather than animated actors
- ✅ Create 3–5 static mesh permutations per character type to give the army visual variety without animation cost
- ✅ Use the "Combine Static Meshes" option when downloading GLB models from Sketchfab to keep imports clean
- ✅ Add props as child Static Mesh components of the character actor so they move, rotate, and scale together
- ✅ Use transform copy/paste rather than manual placement when attaching the same prop to many characters
- ✅ Organize character static meshes, prop meshes, and materials into clearly named folders in the Content Browser

#### Keep In Mind

- "Make Static Mesh" bakes the current pose or frame of a skeletal mesh into a static mesh; it does not retain animation data
- Static mesh permutations are different models, not material swaps; each permutation increases content size
- Copy/paste transforms applies Location, Rotation, and Scale together; you can copy fields individually if only one needs to match
- A Static Mesh component added to an actor hierarchy automatically follows the actor's transforms in the level

#### Security & Safety Notes

- Only download Sketchfab models that you have the rights to use in your projects
- Verify that downloaded GLB files are from trusted Sketchfab authors and do not contain hidden malicious metadata
- Avoid downloading executables or tools from Sketchfab; only download the 3D model files themselves
- Keep a backup of original skeletal mesh assets before converting them to static meshes

#### Common Pitfalls

- **Problem:** The Pattern tool does not accept the character because it is still a skeletal mesh actor
  **Solution:** Use "Make Static Mesh" to convert the skeletal mesh to a static mesh before patterning
- **Problem:** The army looks too repetitive with identical character poses
  **Solution:** Create 3–5 static mesh permutations from different animation frames and let the Pattern tool randomly or sequentially assign them
- **Problem:** The blaster prop does not move with the character when the actor is transformed
  **Solution:** Add the blaster as a Static Mesh component inside the character Blueprint or actor hierarchy, not as a separate placed actor
- **Problem:** Manual prop placement on every character takes too long and drifts out of alignment
  **Solution:** Use transform copy/paste on the Static Mesh component to replicate position, rotation, and scale exactly across all characters
- **Problem:** Imported GLB model arrives as dozens of separate meshes
  **Solution:** Re-download from Sketchfab with "Combine Static Meshes" enabled to get a single static mesh asset

### Lesson 2: Building Army Formations with the Pattern Tool

#### Examples

##### Example 1: Building a Basic Grid Formation

Use the Pattern tool on the Modeling tab to arrange soldier static meshes into a rectangular grid, setting Count and Extent values to control rows and spacing.

##### Example 2: Adding Jitter for Organic Variation

Enable Jitter in the Pattern tool settings and adjust Scale, Rotation, and Translation jitter amounts so that each soldier in the formation looks slightly different in size, orientation, and position, avoiding a robotic uniform appearance.

##### Example 3: Organizing Pattern Groups into Folders

After creating a Pattern group, rename and organize the resulting instances into dedicated folders in the World Outliner or Content Browser so large armies remain manageable.

##### Example 4: Mirroring an Army Formation with Transform Mirror

Select half of the army formation and use Right Click > Transform > Mirror to reflect the soldiers across an axis, instantly doubling the formation size while maintaining perfect symmetry.

##### Example 5: Using Pattern Grid Layouts for Complex Formations

Switch the Pattern tool type from Line to Grid, set X and Y counts and extents, and generate a two-dimensional block of soldiers with controllable spacing between rows and columns.

#### Step 1: Select the Base Character Static Mesh

In the UE5 viewport, select the static mesh character actor or blueprint instance that will serve as the base for the Pattern tool. Make sure it is placed at the desired starting position.

#### Step 2: Open the Pattern Tool

With the base character selected, open the Modeling tab. Navigate to XForm > Pattern. The Pattern panel opens with options for Type, Axis, Count, Extent, and Jitter.

#### Step 3: Configure the Grid Layout

Set the Pattern Type to Grid. Set the Count for X and Y to define the number of soldiers per row and column. Adjust the Extent values to control the spacing between soldiers. Use a small positive Extent so soldiers do not overlap.

#### Step 4: Enable and Adjust Jitter Settings

In the Pattern panel, expand the Jitter section. Enable Jitter for Scale, Rotation, and Translation. Set small values for each:
- Scale Jitter: 0.05–0.15 (5–15% size variation)
- Rotation Jitter: 2–5 degrees
- Translation Jitter: 5–20 cm depending on scene scale
These ranges are enough to break up uniformity without making the formation look chaotic.

#### Step 5: Apply the Pattern and Organize Instances

Click Apply or Confirm to generate the army formation. The Pattern tool creates a group of instances. Rename the group in the World Outliner (e.g., "Army_Squad_A"). Drag the group into a dedicated folder in the World Outliner to keep the scene hierarchy clean.

#### Step 6: Mirror the Formation

Select the Pattern group or half of the army formation. Right-click and choose Transform > Mirror. Experiment with the X, Y, and Z axes to find the reflection axis that correctly places the mirrored half. After mirroring, use Local or World space to fine-tune the mirrored group's position so it joins seamlessly with the original formation.

#### Step 7: Create Additional Formation Variants

Repeat the Pattern process with different static mesh permutations (Lesson 1, Step 2) and different Jitter values to create multiple squads. Organize each squad into its own folder in the World Outliner.

#### Best Practices

- ✅ Use a small Extent value in the Pattern Grid so soldiers do not overlap or clip into each other
- ✅ Enable Jitter on Scale, Rotation, and Translation to break up visual repetition in large formations
- ✅ Keep Jitter values conservative; too much jitter makes the army look broken rather than organic
- ✅ Organize Pattern groups into named folders in the World Outliner immediately after creation
- ✅ Use the Modeling tab > XForm > Pattern path to access the tool; it is not a standalone tab
- ✅ Mirror formations from a clean baseline rather than mirroring already-mirrored groups to avoid compound errors

#### Keep In Mind

- The Pattern tool works on static mesh actors and geometry; it does not work on skeletal mesh actors with active animations
- Jitter is applied at creation time; changing Jitter values after the Pattern is baked does not update existing instances
- Grid layout requires both X and Y Count values to be greater than 1; use Count = 1 for a single Line
- Transform Mirror reflects across the chosen axis; you may need to test X, Y, and Z to find the correct visual result
- Pattern groups can be large; use folders to collapse and manage them in the World Outliner

#### Security & Safety Notes

- Always save the scene or level before applying large Pattern operations so you can undo or revert if the result is unsatisfactory
- When mirroring formations, verify the mirrored position does not place soldiers inside walls or other geometry

#### Common Pitfalls

- **Problem:** Pattern tool is greyed out or does not appear in the Modeling tab
  **Solution:** Ensure you have a valid static mesh actor selected; the Pattern tool does not work on skeletal mesh actors or empty selections
- **Problem:** Soldiers overlap or clip into each other after patterning
  **Solution:** Increase the Extent values in the Pattern Grid settings to add more spacing between rows and columns
- **Problem:** The army looks like a block of identical clones
  **Solution:** Enable Jitter for Scale, Rotation, and Translation; use multiple static mesh permutations as the base actor
- **Problem:** Mirrored army is offset from the original formation
  **Solution:** After mirroring, switch to Local or World transform space and manually nudge the mirrored group into alignment
- **Problem:** World Outliner becomes cluttered with hundreds of named instances
  **Solution:** Immediately drag each Pattern group into a named folder after creation; use folders to collapse and hide finished squads

### Lesson 3: Enabling and Debugging Nanite for High-Polygon Performance

#### Examples

##### Example 1: Enabling Nanite on a High-Poly Static Mesh

Right-click a static mesh asset in the Content Browser, choose "Enable Nanite," and confirm so the mesh can render millions of polygons with automatic dynamic LOD and cluster-based culling.

##### Example 2: Fixing Nanite Shadow Artifacts in Ray Tracing

If shadows appear blocky or incorrect when ray tracing is enabled with Nanite meshes, open the UE5 console and set `r.RayTracing.Nanite.Mode 1` to force ray tracing to use the streamed mesh instead of the fallback, eliminating shadow artifacts.

##### Example 3: Using Nanite Visualization Modes to Inspect Triangle Counts

Switch the viewport to a Nanite visualization mode to see the live triangle count, cluster boundaries, and LOD transitions on Nanite-enabled meshes, confirming that the expected polygon budget is being respected at runtime.

#### Step 1: Enable Nanite on a Static Mesh

In the UE5 Content Browser, locate the static mesh you want to enable Nanite on. Right-click the asset and select "Enable Nanite." Confirm the operation in the pop-up dialog. Nanite will now manage LOD and culling for this mesh automatically.

#### Step 2: Verify Nanite in the Viewport

Place the Nanite-enabled static mesh in the level. In the UE5 viewport, open the Show flags or view mode dropdown and look for Nanite-specific visualization options. Confirm that the mesh renders correctly and that triangle counts drop as the camera moves away.

#### Step 3: Trigger and Identify Nanite Shadow Artifacts

If you have ray tracing enabled in the project, render the scene and observe shadows cast by Nanite meshes. Blocky, missing, or incorrectly shaded shadows on or around Nanite meshes indicate that ray tracing is falling back to a lower-quality representation of the mesh.

#### Step 4: Fix Shadow Artifacts with the Console Variable

Open the UE5 console (typically with the tilde `~` key). Enter the command:
```
r.RayTracing.Nanite.Mode 1
```
This forces ray tracing to trace against the streamed Nanite mesh data instead of the fallback representation, restoring correct shadow rendering.

#### Step 5: Inspect Triangle Counts with Nanite Visualization

In the viewport, switch to a Nanite visualization mode. Use the mode that displays triangle counts or cluster density. Move the camera closer to and farther from the mesh to observe how the visible triangle count changes dynamically with distance and screen size, confirming that Nanite is active and functioning.

#### Best Practices

- ✅ Enable Nanite on high-poly static meshes that exceed 100k triangles to gain automatic LOD and culling
- ✅ Use `r.RayTracing.Nanite.Mode 1` when ray tracing is enabled and Nanite shadow artifacts appear
- ✅ Inspect Nanite visualization modes during development to confirm expected triangle budgets and cluster behavior
- ✅ Keep Nanite-enabled meshes as static mesh assets rather than skeletal meshes; Nanite does not support skeletal deformation
- ✅ Test Nanite meshes at multiple camera distances to verify dynamic LOD is working correctly

#### Keep In Mind

- Nanite is a UE5 virtualized geometry technology designed for static meshes; it does not support skeletal meshes or animated characters
- Nanite handles millions of polygons through cluster-based culling and streaming; the artist does not need to manually create LODs
- `r.RayTracing.Nanite.Mode 1` is a console variable that persists for the current session and may need to be re-entered after restarting the editor
- Nanite visualization modes are found in the UE5 viewport Show menu and are useful for debugging but are not intended for final shipped builds

#### Security & Safety Notes

- Console variables can affect rendering stability; if a console command causes crashes or rendering errors, restart the editor and re-enter the command carefully
- Do not enable Nanite on extremely dense meshes without testing target hardware performance; Nanite streaming has a minimum overhead cost
- Only use Nanite visualization modes for debugging; disable them before capturing final screenshots or builds

#### Common Pitfalls

- **Problem:** Nanite option is missing when right-clicking a static mesh
  **Solution:** Ensure the project is using UE5; Nanite is not available in UE4. Also confirm the static mesh is not already Nanite-enabled or disabled in project settings
- **Problem:** Nanite-enabled mesh shows blocky or missing shadows with ray tracing enabled
  **Solution:** Enter `r.RayTracing.Nanite.Mode 1` in the UE5 console to force ray tracing to use the streamed mesh instead of the fallback
- **Problem:** Triangle count does not change when moving the camera away from a Nanite mesh
  **Solution:** Verify Nanite is actually enabled on the mesh asset, not just on the level instance; check the Nanite visualization mode is active
- **Problem:** Performance drops after enabling Nanite on many meshes
  **Solution:** Enable Nanite only on meshes that genuinely need it; test on target hardware and consider cluster size and triangle density per mesh
- **Problem:** Console variable setting does not stick between editor sessions
  **Solution:** Console variables are session-only by default; add the command to the project's DefaultEngine.ini ConsoleVariables section if persistence is required

## Glossary / Index

| Term | Definition |
|---|---|
| Actor | A UE5 level object that can be placed, transformed, and scripted; characters and props are both actors |
| Animation Frame | A single pose snapshot from a character animation sequence that can be baked into a static mesh permutation |
| Blaster Prop | A weapon or accessory model downloaded from Sketchfab and attached to a character as a Static Mesh component |
| Combine Static Meshes | A Sketchfab download option that merges a GLB model's separate parts into a single static mesh for cleaner UE5 import |
| Console Variable | A runtime or editor setting in UE5 controlled via the console, such as `r.RayTracing.Nanite.Mode 1`, used to adjust rendering behavior without recompiling |
| Copy/Paste Transforms | A UE5 workflow for duplicating Location, Rotation, and Scale values between components or actors by right-clicking transform fields |
| Dynamic LOD | Automatic level-of-detail adjustment that changes mesh complexity based on camera distance and screen coverage, managed by Nanite without manual LOD authoring |
| Folders | Organizational containers in the UE5 World Outliner or Content Browser used to group and collapse related actors or assets |
| GLB | A binary 3D file format (GL Transmission Format Binary) used to transfer meshes, materials, and scene data between tools like Sketchfab and UE5 |
| Grid Layout | A two-dimensional Pattern tool arrangement with configurable X and Y counts and extents for building rectangular formations |
| Jitter | Pattern tool settings that add random variation to Scale, Rotation, and Translation per instance to break up visual uniformity |
| Make Static Mesh | A UE5 right-click context menu command that converts a skeletal mesh or other mesh into a static mesh asset |
| Nanite | UE5's virtualized geometry technology that handles millions of polygons through cluster-based streaming and culling for static meshes |
| Nanite Shadow Artifacts | Blocky, missing, or incorrectly shaded shadows that appear when ray tracing interacts with Nanite meshes without the correct console variable setting |
| Nanite Visualization Modes | UE5 viewport modes used to inspect Nanite triangle counts, cluster boundaries, and LOD transitions during development |
| Pattern Tool | A Modeling tab > XForm tool in UE5 that creates linear, grid, or circular arrays of selected geometry with controllable count, spacing, and jitter |
| Permutation | A distinct static mesh variant created by baking a different animation frame of a character, used to add visual variety to army formations |
| Props | 3D objects such as weapons or accessories attached to characters as Static Mesh components so they move together |
| r.RayTracing.Nanite.Mode 1 | A UE5 console variable command that forces ray tracing to use the streamed Nanite mesh data, fixing shadow artifacts |
| Ray Tracing | A rendering technique that simulates light paths for accurate reflections, shadows, and global illumination; can interact with Nanite meshes |
| Rotation | One of the three transform axes (X, Y, Z) controlling an object's orientation; copy/paste rotation ensures props face the same direction on every character |
| Scale | One of the three transform axes controlling an object's size; Jitter Scale adds variation to instance sizes in the Pattern tool |
| Skeletal Mesh | A UE5 mesh bound to a skeleton that can be animated; must be converted to a static mesh before it can be patterned |
| Sketchfab | An online platform for hosting, sharing, and downloading 3D models, including characters and props used in this chapter |
| Static Mesh | A UE5 mesh asset without skeleton or animation data, suitable for patterning, merging, and Nanite-enabled rendering |
| Static Mesh Component | A UE5 component added to an actor Blueprint or level actor that holds a static mesh asset, allowing props to be parented and transformed with the actor |
| Transform Mirror | A right-click transform operation in UE5 that reflects selected actors or Pattern groups across a chosen axis for symmetrical duplication |
| Translation | One of the three transform axes (X, Y, Z) controlling an object's position; Jitter Translation adds positional variation to Pattern instances |
| Triangle Counts | The number of polygons rendered for a mesh; Nanite visualization modes display live triangle counts to confirm LOD behavior |
| UE5 | Unreal Engine 5, the game engine used for patterning characters, attaching props, enabling Nanite, and debugging rendering in this chapter |
