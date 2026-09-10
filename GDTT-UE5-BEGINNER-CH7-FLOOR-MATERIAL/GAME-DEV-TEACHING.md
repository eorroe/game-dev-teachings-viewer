# Game Dev Teaching Title

## Overview

This chapter teaches how to create a non-repetitive floor material for a spaceship hangar in Unreal Engine 5 using free Megascans assets imported through Quixel Bridge. It covers converting starter content material properties into configurable parameters, leveraging the ORM texture workflow, and using material instances for real-time tweaking without reopening the material graph. By the end, you will understand why texture repetitiveness is a critical problem on large surfaces and how to solve it using variation and imperfection nodes.

## When to Follow Game Dev Teachings

- When you need to import high-quality materials into UE5 from Quixel Bridge
- When working on large surfaces that exhibit visible texture repetition
- When the user asks how to use material instances and exposed parameters for real-time control
- When you want to understand the ORM texture workflow and how to apply it to custom materials
- When fixing overly glossy or dull surfaces using Min/Max roughness parameters
- When converting existing material graphs into reusable, parameter-driven material instances

## Lessons From Game Dev Teachings

### Lesson 1: Importing Materials from Quixel Bridge and Setting Up the Floor

#### Examples

##### Example 1: Importing Megascans Surface Materials

Quixel Bridge is accessible directly from within the Unreal Engine toolbar and provides approximately 15,000 free assets including 3D meshes, textures, and imperfections up to 8K resolution. When a material is imported through Quixel Bridge, it automatically arrives as a Material Instance rather than a parent material. Epic Games preconfigured a single parent material with all common parameters, so each imported asset is a child instance that exposes tiling, metallic, roughness, and other properties without requiring graph editing.

##### Example 2: Repetitive Texture on a Large Hangar Floor

When a Megascans material is applied to a large floor mesh without tiling adjustment, the texture repeats visibly across the entire surface. On the scale of a spaceship hangar, this creates an obvious, toy-like appearance that breaks realism. Increasing the tiling values (e.g., UV scale of 23 on X and 33 on Y) spreads the texture across the surface, but repetition can still remain if imperfection and variation nodes are not applied.

#### Step 1: Access Quixel Bridge and Sign In

Navigate to the Quixel Bridge icon in the top toolbar of Unreal Engine. Ensure you are signed in before importing assets. Quixel Bridge will open a catalog of assets organized by genre and category. To find a specific surface, use the search bar or browse the Surfaces category.

#### Step 2: Search and Download a Megascans Surface Material

Search for the desired material type, such as "Metal Panel Facade." Locate the specific asset to use and open its detail panel. Select the highest available texture quality (up to 8K) for best results. Click Download if the asset has not been downloaded previously. Once downloaded, the Add button becomes enabled.

#### Step 3: Add the Material to the Project

Click the Add button in Quixel Bridge. The engine automatically creates a new folder structure under the MegaScans folder (e.g., MegaScans > Surfaces > Metal_Panels_Facade) and places the imported Material Instance there. The imported material is a child of Epic's shared parent material that exposes all common parameters.

#### Step 4: Create a Floor Mesh

Create a cube or plane mesh, reset its transform, scale it to the desired floor size, and position it below the hangar geometry. Rename the mesh to "Floor" and move it into the appropriate project folder (e.g., Spaceship) for organization.

#### Step 5: Apply the Material Instance and Adjust Tiling

Drag the imported Quixel Material Instance onto the floor mesh. Open the instance and adjust the Tiling parameter. Use different X and Y values (e.g., 23 and 33) to create a slightly stretched, non-uniform tiling that matches the reference look. This breaks up the mathematical repetition of the texture coordinates.

#### Step 6: Adjust Min/Max Roughness for Surface Dullness

Open the Material Instance parameters and locate Min Roughness and Max Roughness. By default, Max Roughness is 1.0 and Min Roughness is 0.0, producing a fully glossy surface. Reduce Max Roughness (e.g., to 0.5) and set Min Roughness (e.g., to 0.3) to make the surface less dull and restore realistic light reflections.

#### Step 7: Open the Starter Content Material and Observe Variation Nodes

Open the UE5 Starter Content material "M_Burnished_Steel" to examine its graph. At the top of the material graph, notice three Texture Sample nodes feeding into a blend network that mixes imperfection and variation textures with the base color and roughness. These variation textures at large, medium, and small scales are responsible for eliminating visible repetition. Hiding or bypassing these nodes causes the material to repeat exactly, proving their necessity on large surfaces.

#### Step 8: Duplicate the Starter Material and Replace Textures

Duplicate the Starter Content material and rename it (e.g., "Floor_Material"). Open the duplicated material and use the Find and Select feature (Ctrl+Space) to swap the color and normal map texture inputs with the Megascans floor textures. Do not remove or alter the variation and imperfection nodes at the top of the graph.

#### Step 9: Connect the ORM Texture

Locate the Megascans ORM texture in the content browser. Understand that ORM stores Occlusion in the red channel, Roughness in the green channel, and Metallic in the blue channel. Connect the green channel of the ORM texture to the Roughness input. If the original Megascans asset stores roughness in the alpha channel instead, the ORM texture's green channel replaces that alpha-based connection.

#### Step 10: Connect Ambient Occlusion from ORM

Connect the red channel of the ORM texture to the Ambient Occlusion input on the material. This adds contact shadow detail and darkens crevices, improving depth perception.

#### Step 11: Create a Material Instance for Real-Time Control

Right-click the new parent material and select "Create Material Instance." Apply this instance to the floor mesh. Any parameter that was converted to a material parameter in the parent graph can now be controlled directly in the instance panel without reopening the material editor.

#### Step 12: Convert Material Graph Values to Parameters

In the parent material graph, select nodes such as the Min Roughness and Max Roughness values, right-click, and choose "Convert to Parameter." Name each parameter clearly (e.g., "Min_Roughness", "Max_Roughness", "Color_Tint"). In the material instance, these parameters can now be tweaked in real time with immediate visual feedback.

#### Step 13: Adjust Color Tint Using a Multiply Node

To shift the base color of the material, insert a Multiply node between the base color texture and the Base Color input. Connect an RGB node to the Multiply node's second input. Right-click the RGB node and convert it to a parameter named "Color_Tint." Adjust the RGB values in the material instance to tint the floor without modifying the source texture. Values above 1.0 in any channel increase brightness beyond the texture's native range.

#### Best Practices

- ✅ Always use the highest texture quality available in Quixel Bridge for final surfaces.
- ✅ Use slightly different X and Y tiling values to avoid uniform, visible grid repetition.
- ✅ Never remove the variation and imperfection nodes when adapting Starter Content materials to custom assets.
- ✅ Convert Min/Max Roughness and Color Tint to parameters so artists can iterate without opening the material graph.
- ✅ Keep the original Megascans Material Instance as a reference when building custom parent materials.
- ✅ Organize imported assets into MegaScans > Surfaces folders automatically created by Quixel Bridge.
- ✅ Use Ctrl+Space (Find and Select) to quickly swap texture nodes rather than rewiring the graph manually.

#### Keep In Mind

- Quixel Bridge assets arrive as Material Instances by default. The parent material is shared across all Quixel assets and can be reviewed by opening the parent reference in the material instance editor.
- The alpha channel of some Megascans textures stores roughness data. When using an ORM texture instead, use the green channel for roughness and connect the red channel to Ambient Occlusion.
- Variation nodes in the Starter Content use three different tiling scales (large, medium, small) to layer imperfection and break up repetition across the surface.
- Material instances expose only the parameters defined in the parent material graph. If a value is hardcoded and not converted to a parameter, it cannot be adjusted in the instance panel.
- Converting a value to a parameter in the parent graph immediately makes it available in all child instances.

#### Security & Safety Notes

- Ensure your Quixel Bridge account is signed in before attempting to import assets. An unsigned session will prompt for login and block the download and add workflow.
- Do not delete the original Quixel Megascans Material Instance after creating your custom parent material. Keep it as a reference for correct texture connections and parameter setup.
- Always save the material and content browser before closing the editor to avoid losing parameter conversion work.

#### Common Pitfalls

- **Problem:** The floor material looks like plastic or a toy due to visible repetition.
  **Solution:** Increase tiling values and confirm that the variation and imperfection nodes from the Starter Content material are still connected and active in the custom material graph.

- **Problem:** Roughness has no effect because the wrong texture channel is connected.
  **Solution:** Verify whether roughness is stored in the alpha channel or the green channel of the ORM texture. Disconnect the alpha input and connect the green channel of the ORM texture to the Roughness input instead.

- **Problem:** Material instance parameters are greyed out and cannot be edited.
  **Solution:** The corresponding values in the parent material graph have not been converted to parameters. Open the parent material, select the value node, right-click, and choose "Convert to Parameter."

- **Problem:** The floor is too glossy and reflects too much light.
  **Solution:** Reduce Max Roughness and increase Min Roughness in the material instance (e.g., Min 0.3, Max 0.5) to dull the surface and restore realistic reflections.

- **Problem:** Tiling on one axis causes stretching artifacts.
  **Solution:** Use non-uniform tiling values (different X and Y scales) to match the reference and avoid axis-aligned stretching that reveals the texture grid.

## Glossary / Index

|Term|Definition|
|----|----------|
|Ambient Occlusion|A shading technique that darkens crevices and contact points to simulate soft global illumination shadows; in ORM workflows it is stored in the red channel.|
|Base Color|The diffuse albedo texture that defines the surface color without lighting information.|
|Color Tint|A parameter-driven RGB multiply used to shift the hue or brightness of a base color texture without editing the source texture file.|
|Material Graph|The node-based visual scripting environment inside Unreal Engine used to construct shaders and define material behavior.|
|Material Instance|A lightweight child of a parent material that exposes only the parameters defined in the parent, allowing real-time editing without modifying the graph.|
|Megascans|A library of high-quality 3D assets, textures, and materials provided by Quixel and integrated into Unreal Engine through Quixel Bridge.|
|Min/Max Roughness|Two scalar parameters that define the roughness range of a surface; values closer to 0.0 are glossy, while values closer to 1.0 are dull.|
|Normal Map|A texture that encodes surface detail as perturbed normals to simulate bumps, scratches, and depth without adding geometry.|
|Occlusion|See Ambient Occlusion; in the ORM texture it is stored in the red channel.|
|ORM Texture|A packed texture that stores Occlusion (red), Roughness (green), and Metallic (blue) in a single image to save memory and draw calls.|
|Parent Material|The master material graph that defines the core shader logic and exposed parameters for all child Material Instances.|
|Quixel Bridge|A plugin and standalone application integrated with Unreal Engine for browsing, downloading, and adding Quixel Megascans assets directly into a project.|
|Roughness|A scalar value controlling how sharp or scattered surface reflections are; in the ORM texture it is stored in the green channel.|
|Texture Repetition|A visual artifact where a tiled texture repeats in a regular, noticeable pattern across a large surface, reducing realism.|
|Tiling|The UV scale applied to a texture to control how many times it repeats across a surface; non-uniform X and Y tiling helps break up visible grid patterns.|
|Variation Nodes|Texture sample nodes in the Starter Content materials that layer large, medium, and small-scale imperfection textures to eliminate repetition and add surface realism.|
|UV Coordinates|The 2D mapping used to project textures onto 3D geometry; tiling scales these coordinates to control texture repetition.|
