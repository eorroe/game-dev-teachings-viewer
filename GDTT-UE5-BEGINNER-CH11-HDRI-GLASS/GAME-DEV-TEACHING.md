# GDTT-UE5-BEGINNER-CH11-HDRI-GLASS

## Overview

This chapter teaches how to use an HDRI (High Dynamic Range Image) as both a scene background and a lighting source in Unreal Engine 5. You will source a free space or planet HDRI from ProductionCrate, import it into the UE5 Content Browser, configure it correctly, and use the HDRI Backdrop actor to build a realistic Earth-from-space scene. The chapter also covers creating a glass window on a spaceship using Starter Content glass materials and managing visual quality versus performance using UE5's Scalability settings and post-process reflection controls.

## When to Follow Game Dev Teachings

- When you need to set up a skybox or environment background in UE5
- When working with outdoor or space scenes that require realistic lighting from an HDRI
- When the user asks about importing and configuring HDR files in Unreal Engine 5
- When adding glass or reflective surfaces to a spaceship or vehicle scene
- When adjusting post-process settings to balance visual fidelity with performance

## Lessons From Game Dev Teachings

### Lesson 1: Importing and Configuring an HDRI in UE5

#### Examples

##### Example 1: Importing an HDRI from ProductionCrate

1. Go to ProductionCrate and download a free space or planet HDR file.
2. In UE5, open the Content Browser and click Import to bring the `.hdr` file into your project.
3. After importing, select the HDR asset and set its Mip Gen Settings to **"No MIP Maps"** in the Details panel. This prevents the HDR from being compressed and losing detail.
4. Drag the HDR asset into the scene or use it as a texture source for an HDRI Backdrop actor.

##### Example 2: Using the HDRI Backdrop Actor

1. In the UE5 Place Actors panel, search for and place an **HDRI Backdrop** actor into the scene.
2. By default, the HDRI Backdrop uses a simple dome mesh. Replace the default dome with a **SkySphere** from Starter Content for a more realistic full-sky appearance.
3. Assign the imported HDRI texture to the HDRI Backdrop's texture slot.
4. Adjust the **Intensity** and **Size** values. For a realistic Earth-from-space distance, a size around **3500** is recommended.
5. Rotate the HDRI by selecting the HDRI Backdrop actor and pressing the **E** key to enter rotation mode. Fine-tune the HDRI's position using the **Projection Center X, Y, and Z** values in the Details panel.

#### Steps

1. **Source the HDRI file.** Download a free space or planet HDR from ProductionCrate or a similar free asset library.
2. **Import the HDR into UE5.** Open the Content Browser and use Import to add the `.hdr` file.
3. **Disable MIP Maps.** Select the imported HDR asset. In the Details panel, find the Texture group settings and set **Mip Gen Settings** to **"No MIP Maps"**. This preserves the full dynamic range and detail of the image.
4. **Place an HDRI Backdrop actor.** Search the Place Actors panel for "HDRI Backdrop" and drag it into the viewport.
5. **Replace the default dome with a SkySphere.** Remove or hide the default dome mesh. Place a **SkySphere** from Starter Content and scale or position it to surround the scene. Assign the HDRI texture to the SkySphere material.
6. **Adjust HDRI intensity and size.** In the HDRI Backdrop actor's Details panel, set the **Intensity** to control brightness and the **Size** to control the apparent distance of the sky. A size of approximately **3500** creates a convincing Earth-from-space scale.
7. **Rotate and position the HDRI.** Press **E** with the HDRI Backdrop selected to rotate the actor. Fine-tune the projection center using **Projection Center X/Y/Z** to align the horizon or key visual features.
8. **Create a glass window on a spaceship.** Duplicate a cube mesh in the scene and scale it to represent a window. Apply a glass material from Starter Content, such as **M_Glass_Material_Inst**.
9. **Test multiple glass materials.** UE5 Starter Content includes several glass material variations. Apply each one and evaluate which provides the best reflections and visual result for the scene.
10. **Adjust post-process reflection settings.** Open the Post Process Volume settings and tune reflection intensity and quality. Higher settings improve visuals but impact FPS.
11. **Manage performance with Scalability settings.** For lower-end hardware, switch UE5's Scalability preset from **Cinematic** to **High** or **Medium** to reduce the performance cost of reflections and other expensive rendering features while keeping the scene visually acceptable.

#### Best Practices

- ✅ Always set Mip Gen Settings to "No MIP Maps" for HDR textures used as environment lighting
- ✅ Use the SkySphere from Starter Content rather than the default HDRI Backdrop dome for full-coverage skies
- ✅ Set HDRI size to around 3500 for realistic space-Earth distances
- ✅ Test multiple glass material options from Starter Content to find the best fit for reflections
- ✅ Use Cinematic quality for high-end machines and drop to High or Medium for lower-end hardware
- ❌ Do not leave MIP Maps enabled on HDR textures used for scene lighting — it degrades the HDR range
- ❌ Do not set post-process reflection quality too high on lower-end hardware without checking FPS impact
- ❌ Avoid using the default HDRI Backdrop dome without replacing it with a SkySphere for full sky scenes

#### Keep In Mind

- The HDRI Backdrop actor's rotation is controlled in world space by selecting the actor and pressing the E key.
- The Projection Center X, Y, and Z values are used to fine-tune where the HDRI projection is centered in the scene.
- MIP Maps are useful for regular textures but harmful for HDR environment maps because they reduce the precision of the high dynamic range data.
- Glass materials in UE5 Starter Content are material instances that can be adjusted without recompiling shaders.
- Scalability settings in UE5 allow you to predefine quality presets (Cinematic, High, Medium, Low) that control shadows, reflections, anti-aliasing, and other expensive features.
- Post-process reflections are one of the most FPS-intensive rendering features; always profile performance after adjusting them.

#### Security & Safety Notes

- Only download HDR files from trusted sources such as ProductionCrate or UE5's own marketplace.
- Do not execute or run HDR files — they are image/texture assets consumed only by the engine.
- When sharing a project that uses third-party HDRIs, verify that the license permits commercial use if applicable.

#### Common Pitfalls

- **Problem:** The HDRI looks blurry or washed out after importing.
  **Solution:** Set Mip Gen Settings to "No MIP Maps" on the HDR texture asset and re-save.
- **Problem:** The sky appears as a small dome instead of a full surrounding sky.
  **Solution:** Replace the default HDRI Backdrop dome mesh with a SkySphere from Starter Content and increase the Size value (try ~3500).
- **Problem:** Glass windows appear opaque or non-reflective.
  **Solution:** Ensure a proper glass material instance (such as M_Glass_Material_Inst) is applied and that the mesh has correct UVs. Test other Starter Content glass materials if needed.
- **Problem:** Frame rate drops significantly after enabling high-quality reflections.
  **Solution:** Lower the post-process reflection quality or switch the project's Scalability setting from Cinematic to High or Medium.

## Glossary / Index

| Term | Definition |
|---|---|
| Cinematic | The highest UE5 Scalability preset, enabling maximum visual quality at the cost of performance |
| Content Browser | The UE5 panel used to import, organize, and manage all project assets |
| FPS | Frames Per Second; a measure of rendering performance |
| Glass Material | A UE5 material designed to simulate transparent, reflective surfaces such as windows |
| HDRI | High Dynamic Range Image; an image format that stores a wider range of luminance values, used in UE5 as both a background and a lighting source |
| HDRI Backdrop | A UE5 actor that displays an HDRI texture as the scene sky and contributes environment lighting |
| HDR File | The `.hdr` texture file format used for high dynamic range images |
| Intensity | An HDRI Backdrop property that controls the brightness of the HDRI lighting in the scene |
| Mip Gen Settings | Texture import settings that control whether MIP Maps are generated; set to "No MIP Maps" for HDR environment textures |
| MIP Maps | Pre-filtered, down-scaled versions of a texture used to improve rendering performance at a distance |
| Post Process Volume | A UE5 volume actor that applies screen-space effects such as reflections, bloom, and color grading |
| ProductionCrate | A website offering free 3D assets, including HDR space and planet textures for game development |
| Projection Center X/Y/Z | HDRI Backdrop properties that fine-tune the 3D center position of the HDRI projection in the scene |
| Scalability | UE5 quality presets that control rendering feature levels (e.g., Cinematic, High, Medium, Low) to balance visual fidelity and performance |
| SkySphere | A Starter Content mesh used to display a full surrounding sky texture in UE5 |
| Space HDRI | An HDR environment image capturing a space or planetary scene, used for skybox and lighting in UE5 |
| Starter Content | A set of default UE5 assets including meshes, materials, and textures available in new projects |
| UE5 | Unreal Engine 5, a real-time 3D creation platform used for game development and visualization |
