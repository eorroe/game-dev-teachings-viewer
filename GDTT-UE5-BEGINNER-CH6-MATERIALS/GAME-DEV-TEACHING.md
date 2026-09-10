# GDTT-UE5-BEGINNER-CH6-MATERIALS

## Overview

This chapter teaches the fundamentals of creating and working with materials in Unreal Engine 5, covering material graph basics, key material properties such as Base Color, Metallic, Specular, Roughness, and Emissive, and how to use common nodes like RGB, Value, Multiply, and more. It also covers creating material instances from a parent master material to enable rapid iteration, importing texture maps from online sources such as textures.com, and resolving common texture tiling issues using the MF Tiling node for UV control.

## When to Follow Game Dev Teachings

- When creating your first UE5 material from scratch and need a clear walkthrough of the material graph and output node
- When learning how to control surface properties like metallic, specular, roughness, and emissive color using value and RGB nodes
- When setting up a master/parent material and child material instances to rapidly create material variants
- When importing texture maps (Albedo, Normal, Roughness, Metallic, AO/ORM) from an online source and need to connect them correctly in the material graph
- When textures appear stretched or tiling incorrectly and need to use the MF Tiling node to control UV repetition

## Lessons From Game Dev Teachings

### Lesson 1: Creating UE5 Materials From Scratch and Material Graph Basics

#### Examples

##### Example 1: Basic Box Material With Base Color

Right-click in the Content Browser, navigate to Materials, and create a new Material named "MM_Box" (master material). Drag and drop the material onto a mesh in the viewport to apply it. Double-click the material to open the Material Editor, which shows a 3D viewport on the left and the material graph on the right. The output node is the final node all other nodes connect into. Create an RGB node (shortcut: three left-clicks in empty graph space), connect its output to Base Color on the Material Output node, double-click the RGB node to set a color (e.g. red), then click Apply at the top left to see the change in the viewport.

##### Example 2: Adjusting Metallic, Specular, and Roughness

Create a Value node (shortcut: one left-click) for Metallic and connect it to the Metallic input. A value of 0 means non-metallic, 1 means fully metallic. Duplicate the node (Ctrl+D) or create a new Value node for Specular, connect it to Specular, and set it to 1 to see bright reflections. Create another Value node for Roughness, connect it to Roughness, set it to 0 for a glossy/mirror-like surface and 1 for a fully rough/dull surface. Always click Apply to see changes in real time.

##### Example 3: Emissive Color With Multiply Node for Intensity

Create an RGB node and connect it to Emissive Color. Set it to white or red to see the surface emit light. To control intensity, create a Multiply node (shortcut: press M then left-click), connect the RGB node to one input, and a Value node to the other input. Increasing the value (e.g. 3 or 5) multiplies the emissive output, making the surface glow brighter. Disable a node temporarily by Ctrl+clicking the connection wire.

#### Step 1: Create and Open a New Material

Right-click in the Content Browser, choose Materials from the context menu, name it (e.g. MM_Box), and double-click it to open the Material Editor.

#### Step 2: Set Base Color Using an RGB Node

Press three left-clicks in empty graph space to spawn an RGB node. Connect its output to the Base Color input on the Material Output node. Double-click the RGB node to pick a color from the color wheel or enter a hex value. Click Apply to update the viewport.

#### Step 3: Adjust Metallic, Specular, and Roughness With Value Nodes

Press one left-click to spawn a Value node. Connect it to Metallic and set the value between 0 and 1. Repeat for Specular (controls highlight sharpness) and Roughness (0 = glossy/mirror, 1 = rough/dull). Use Ctrl+D to duplicate existing value nodes when possible.

#### Step 4: Add Emissive Light With a Multiply Node for Intensity

Press three left-clicks to add an RGB node, connect it to Emissive Color. To boost intensity, press M then left-click to add a Multiply node. Connect the RGB node to one input and a Value node (one left-click) to the other input. Connect the Multiply output to Emissive Color. Increase the value node to intensify the glow. Click Apply after each change.

#### Step 5: Create a Material Instance (Child Material)

Right-click the master material (e.g. MM_Box) in the Content Browser and select Create Material Instance. Name it (e.g. MI_Box). Drag the instance onto a mesh to apply it. Double-click the instance to open it — it does not show a graph, only parameter slots inherited from the parent.

#### Step 6: Convert Nodes to Parameters in the Parent Material

In the master material graph, right-click a node (such as an RGB node or Value node) and choose Convert to Parameter. Name the parameter clearly (e.g. BaseColor, Metallic, Roughness). Save and apply the master material. Now the Material Instance will expose those parameters in its editor, letting you change colors and values without reopening the graph.

#### Step 7: Import Textures and Connect Texture Maps

Download texture packs (Albedo/Base Color, Normal, Roughness, Metallic, Ambient Occlusion) from an online source such as textures.com. Import the PNG files into UE5. In the material graph, right-click and search for each texture sample node. Connect the Albedo/Base Color texture RGB output to Base Color. Connect the Normal texture to Normal. Connect Roughness, Metallic, and AO textures to their respective inputs. If using a packed ORM (Occlusion/Roughness/Metallic) texture, use the appropriate channels (commonly Red=Roughness, Green=Metallic, Blue=AO) or split channels to route values correctly.

#### Step 8: Fix Tiling Using the MF Tiling Node

If textures appear stretched or repeat incorrectly, use an MF Tiling node to control UV tiling. Insert it between the texture sample and the material input, or connect it to the UVs input of the texture sample to scale the texture repetition independently on U and V axes.

#### Best Practices

- ✅ Always organize materials in a dedicated Materials folder in the Content Browser
- ✅ Name master materials with an MM_ prefix and material instances with an MI_ prefix for clarity
- ✅ Convert frequently changed values to parameters early so instances expose them
- ✅ Use Multiply nodes to scale emissive intensity rather than hardcoding extreme RGB values
- ✅ Download textures from reputable PBR sources and keep maps in a consistent naming convention
- ✅ Verify that Normal maps are imported with the correct format (e.g. Normal map compression)
- ✅ Use the MF Tiling node to fix stretched textures instead of scaling the mesh UVs in a 3D app

#### Keep In Mind

- The Material Editor viewport updates in real time as you drag nodes, but you must still click Apply for changes to persist
- Ctrl+click a connection wire to temporarily disable a node or branch without deleting it
- Not all node types support conversion to parameters; RGB, scalar, and texture sample nodes typically do
- Material Instances inherit everything from the parent except the parameters you expose — changes to the parent propagate to all children
- Ambient Occlusion (AO) darkens crevices and contact points; it is often packed together with Roughness and Metallic into a single ORM texture to save draw calls

#### Security & Safety Notes

- Only download texture packs from trusted sources; inspect files before importing into the project
- Do not import or use textures with embedded scripts or non-image file formats
- Keep project content organized to avoid overwriting shared master materials accidentally
- UE5 project files and assets should not be shared publicly if they contain licensed or proprietary content

#### Common Pitfalls

- **Problem:** Material changes do not appear in the level viewport
  **Solution:** Always click Apply in the Material Editor after making graph changes
- **Problem:** Material Instance editor shows no editable parameters
  **Solution:** Convert the relevant nodes in the parent master material to parameters before opening the instance
- **Problem:** Textures look stretched or blurry on a mesh
  **Solution:** Check the mesh UVs and use the MF Tiling node to adjust U and V tiling independently
- **Problem:** Emissive material looks dim or washed out
  **Solution:** Use a Multiply node with a value greater than 1 to boost intensity, or verify Lumen and lighting settings in the scene
- **Problem:** Normal map appears flat or wrong orientation
  **Solution:** Ensure the texture is imported as a Normal map and that the green channel is flipped if the mesh normals appear inverted

## Glossary / Index

|Term|Definition|
|----|----------|
|AO (Ambient Occlusion)|A texture or material property that darkens crevices and contact points where surfaces meet, adding depth and realism|
|Base Color|The primary RGB color or albedo texture of a material representing its surface color without lighting information|
|Emissive Color|A material property that makes a surface emit light independently of scene lighting, useful for glowing effects|
|Material Graph|The node-based editor in UE5 where material properties and textures are connected to define the final appearance of a surface|
|Material Instance|A child material that inherits from a parent master material, exposing only specific parameters for fast iteration without editing the full graph|
|Master Material|The parent material that contains the full node graph and all logic, which child material instances inherit from|
|Metallic|A scalar value between 0 and 1 that defines how metallic a surface is; 0 is non-metallic (dielectric) and 1 is fully metallic|
|MF Tiling Node|A UE5 material function used to control the tiling and repetition of UV coordinates, fixing stretched textures|
|Multiply Node|A math node that multiplies two inputs together, commonly used to scale texture intensity or emissive brightness|
|Normal Map|A texture that simulates surface detail by perturbing surface normals, giving the illusion of depth without extra geometry|
|ORM Texture|A packed texture containing Ambient Occlusion (R), Roughness (G), and Metallic (B) channels in a single image to optimize material inputs|
|Parameter|A named, exposed value in a master material that can be edited in a Material Instance without opening the material graph|
|PBR (Physically Based Rendering)|A rendering approach that uses physically accurate material properties like Base Color, Metallic, Roughness, and Normal to achieve realistic results|
|Roughness|A scalar value between 0 and 1 that controls how rough or smooth a surface is; 0 is perfectly smooth/glossy and 1 is fully rough/matte|
|Specular|A scalar value that controls the intensity of specular highlights on a surface, affecting how shiny it appears|
|Texture Sample|A node in the material graph that samples a 2D texture and outputs its color data for use in material properties|
|Tiling|The repetition of a texture across a surface; incorrect tiling causes textures to appear stretched or misaligned|
|UE5|Unreal Engine 5, the game engine used for real-time 3D creation, rendering, and simulation|
|UVs|Two-dimensional coordinates that map a 2D texture onto a 3D mesh surface|
|Value Node|A single float input node in the material graph used to drive scalar properties like Metallic, Specular, or Roughness|
