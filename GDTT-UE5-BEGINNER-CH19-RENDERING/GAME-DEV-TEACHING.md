# Unreal Engine 5 Rendering Settings and Techniques

## Overview

This game dev teaching covers the complete rendering workflow in Unreal Engine 5, from pre-render console variable presets and per-shot lighting adjustments through to the final output using Lumen and Path Tracing. It teaches you how to set up the Movie Render Queue, configure output directories and naming conventions, manage resolution and frame rates, handle multi-camera sequences with camera cut tracks, and lock camera transforms to avoid accidental changes. These skills are essential for producing professional-grade cinematic renders and image sequences in UE5.

## When to Follow Game Dev Teachings

- When you need to set up a cinematic render in Unreal Engine 5 using Lumen or Path Tracing
- When working with multi-camera sequences and need to manage camera cuts in Sequencer
- When the user asks about Movie Render Queue settings, export formats, or output resolution configuration
- When preparing a project for final rendering and wants to avoid common beginner mistakes like rendering only a single camera

## Lessons From Game Dev Teachings

### Lesson 1: Console Variables, Light Quality, and Per-Shot Lighting

#### Examples

##### Example 1: Using Console Variable Presets to Avoid Repetitive Setup

If a project uses console commands to fix nanite shadow artifacts and ray tracing culling, those values must be re-entered every time the project is opened. Save them as a preset via Window > Console Variables so they load automatically on project open, removing the need to manually retype commands each session.

##### Example 2: Fixing Flickering Shadows with Light Sample Adjustments

In a project with MetaHuman digital avatars, shadows appeared noisy and background lights flickered during renders. Increasing the Samples Per Pixel value on individual lights (tried values of 3, 4, and 5 in Epic's own sample projects) resolved the flickering and improved shadow quality without requiring scene-wide changes.

##### Example 3: Adding Per-Shot Lighting for Cinematic Impact

For a specific camera shot where the scene appeared overly white, a rectangular red light was added facing the characters to simulate the red emergency lighting of an opening spaceship door. Adjusting the light intensity and width created a dramatic color shift visible only during that shot, enhancing narrative pacing before switching to the next camera angle.

#### Step 1: Save Console Variable Presets

Open Window > Console Variables in Unreal Engine 5. Locate the console variables already used in the project (such as those fixing nanite shadow artifacts and ray tracing culling). Select all relevant variables, click Save Preset, create a dedicated folder such as "Console Variables," and name the preset (e.g., "Star Wars"). From this point forward, load the preset at project open rather than re-entering each variable manually.

#### Step 2: Adjust Light Samples Per Pixel for Render Quality

Select any light actor in the scene. Open the Details panel and search for "Samples." Locate the Samples Per Pixel property (default value is 1). Increase this value per light to reduce flickering and shadow noise during renders. Note that higher sample counts impact render performance. Epic's own sample projects commonly use values of 3, 4, or 5. Test different values per scene as the visual difference may be minimal in some scenes and drastic in others.

#### Step 3: Add Per-Shot Lighting Changes

Before committing to the final render, add or modify lights for specific camera shots. For example, add a colored rectangular light aimed at characters for a particular shot to simulate in-scene lighting changes (such as red warning lights during a spaceship door opening). Review the result through the relevant camera, adjust intensity and color to taste, and confirm the lighting change only affects the intended shot's visual narrative.

#### Best Practices

- ✅ Save console variable presets early in the project and reload them on every session
- ✅ Keep Samples Per Pixel at 1 during viewport editing; only raise values before final rendering
- ✅ Add per-shot lighting adjustments before locking cameras so changes are intentional
- ✅ Use the Camera Cut track to verify exactly what will render before starting the Movie Render Queue
- ✅ Disable EXR export during test renders and enable it only for final output
- ✅ Use 4K resolution (3840x2160) for final renders and Full HD (1920x1080) for testing
- ❌ Do not render with JPEG export for final output; it is 8-bit and loses color information
- ❌ Do not leave Screen Percentage at 100% for Lumen renders; set it to 125 or 150 for sharper output
- ❌ Do not increase Path Tracing samples without first testing lower counts in the viewport to understand render time
- ❌ Do not forget to lock camera transforms after final positioning to prevent accidental changes

#### Keep In Mind

- Samples Per Pixel changes affect each light individually, not globally. Adjust each light source separately for best results.
- The Camera Cut track controls exactly which camera is rendered per frame range. Without it, only the first camera in the sequence renders regardless of other cameras present.
- Locking the Camera Cut track in Sequencer prevents accidental camera movement during render review.
- Path Tracing render times are significantly longer than Lumen renders. Render a small frame range or single frame first to gauge duration.
- The Spatial Sample Count and Temporal Sample Count in anti-aliasing multiply together to produce the total samples per pixel for Path Tracing (e.g., 32 x 32 = 1024).

#### Security & Safety Notes

- No user credentials, API keys, or authentication tokens are involved in the rendering workflow described here.
- All rendering is performed locally. Do not share output directories containing rendered sequences publicly without reviewing content rights.

#### Common Pitfalls

- **Problem:** Only one camera appears in the final render despite multiple cameras existing in the scene.
  **Solution:** Configure the Camera Cut track in Sequencer with keyframes for each camera at the correct frame ranges. Use the plus button to add additional cameras to the cut track.
- **Problem:** Camera transforms cannot be locked via right-click after the camera cut track is active.
  **Solution:** Exit the camera cut track, select the individual camera actor, right-click, go to Transform, and select Lock Actor Movement. If the option is not visible, restart the project and try again.
- **Problem:** Path Tracing renders are extremely noisy and take a long time per frame.
  **Solution:** Increase samples gradually in the viewport first to find the minimum sample count that produces a clean image for your scene brightness level. Brighter scenes need fewer samples; darker scenes need more.
- **Problem:** Rendered output appears softer than expected at the set resolution.
  **Solution:** Increase Screen Percentage to 125 or 150 for Lumen renders. This renders at a higher internal resolution and downscales, producing a sharper final image at the same output resolution.

---

### Lesson 2: Movie Render Queue, Output Configuration, and Path Tracing

#### Examples

##### Example 1: Configuring Output Directory and Naming for a Lumen Render

For a Spaceship sequence, the output directory was set to a pre-created Desktop > Renders > Lumen folder. The frame naming was changed from the default full sequence name to "ST" followed by the frame number (ST001, ST002, etc.) by editing the prefix before the dot in the naming field. This produces clean, frame-organized output ready for compositing.

##### Example 2: Switching from Full HD to 4K by Doubling Resolution Values

The render resolution was changed from Full HD (1920x1080) to 4K by multiplying both width and height values by two in the Movie Render Queue output settings, resulting in 3840x2160. This was done for final renders, while Full HD remained the testing resolution for faster iteration.

##### Example 3: Setting a Custom Playback Range to Limit Render Scope

The sequence originally spanned 540 frames, but only the opening door shot needed rendering. Custom Start Frame was set to 0 and Custom End Frame to 300 in the Movie Render Queue, cutting the render workload nearly in half without modifying the Sequencer timeline.

#### Step 1: Open Movie Render Queue and Configure Output Settings

From the Sequencer or Level Editor, open the Movie Render Queue via the render button. Click the Settings button (labeled "unsaved config") to access the full settings panel. Start with the Output section: set the output directory to a prepared folder, configure the file naming prefix (recommend using a short shot code like "ST" followed by frame number), and set the resolution to Full HD for testing or 4K for final output.

#### Step 2: Set Frame Rate and Custom Playback Range

In the Output settings of the Movie Render Queue, set the Frame Rate to the desired value (e.g., 30 FPS). If the sequence is longer than needed, uncheck "Use Sequence Frame Range" and instead set Custom Start Frame and Custom End Frame directly in the render settings to limit rendering to the relevant section.

#### Step 3: Choose Export Format

Remove the default JPEG export setting (8-bit, insufficient for final work). Add PNG export for social media and testing: enable Alpha only if transparency is required, otherwise leave it disabled. For professional post-production in tools like DaVinci Resolve, also add EXR export (16-bit) which preserves far more color data and allows extensive color grading without quality loss.

#### Step 4: Apply Console Variable Preset in Render Settings

In the Movie Render Queue settings, open the Console Variables section. Load the previously saved console variable preset (e.g., "Star Wars") to ensure all required engine settings are active during rendering. Optionally add the `r.ScreenPercentage` console variable to the preset and set it to 125 or 150 for Lumen renders to produce a sharper output image.

#### Step 5: Configure Anti-Aliasing for Path Tracing

For Path Tracing renders, override the project's anti-aliasing method to None. Set the Spatial Sample Count and Temporal Sample Count to values that multiply to the desired total samples per pixel (e.g., 32 x 32 = 1024 samples). Values must be powers of two. Disable Screen Percentage for Path Tracing as it significantly increases render time.

#### Step 6: Set Path Tracing Frame Range

Path Tracing is substantially slower than Lumen. In the Movie Render Queue output settings, reduce the frame range to a small subset (e.g., frames 200 to 203) or a single frame for initial test renders. Evaluate noise, quality, and render duration before committing to a full sequence. For final Path Tracing output, aim for above 1000 samples per pixel for a clean, noise-free image.

#### Step 7: Initiate Local Render and Monitor Output

Click Accept in the settings panel, then click Render Local. During the render, monitor the progress panel on the left for frame count and time remaining. The right panel shows the current frame and active camera cut. Press Escape to stop the render if mistakes are visible in the preview. After rendering completes, review the output sequence using an image sequence viewer such as DJV to confirm quality before proceeding.

#### Best Practices

- ✅ Use JPEG only for quick test renders; switch to PNG or EXR for anything intended for delivery
- ✅ Use Full HD (1920x1080) for testing and 4K (3840x2160) for final renders
- ✅ Set a Custom Playback Range in the Movie Render Queue rather than editing the Sequencer for one-off render ranges
- ✅ Load console variable presets inside the Movie Render Queue settings, not just in the editor viewport
- ✅ Set Screen Percentage to 125-150 for Lumen renders; disable it entirely for Path Tracing
- ✅ Override anti-aliasing to None and configure Spatial/Temporal Sample Count for Path Tracing
- ✅ Render a small frame range first with Path Tracing to gauge total time before rendering the full sequence
- ❌ Do not leave JPEG as the only export format for final cinematic output
- ❌ Do not set Path Tracing samples below what is needed for a clean image; darker scenes require more samples
- ❌ Do not forget to save the project before opening the Movie Render Queue
- ❌ Do not render the full Path Tracing sequence without first testing a single frame for quality and duration

#### Keep In Mind

- The Movie Render Queue settings panel ("unsaved config") is the central hub for all render options; get familiar with its left-side category list and right-side property panel.
- Lumen and Path Tracing settings are mutually exclusive; disable Deferred Rendering (Lumen) before enabling Path Tracer.
- PNG with Alpha disabled is suitable for most social media and preview use cases. EXR is intended for professional color grading workflows.
- Screen Percentage set above 100% for Lumen effectively supersamples the image, resulting in a sharper output at the same resolution but with longer render times.
- Anti-aliasing method must be set to None for Path Tracing because other anti-aliasing methods (such as TSR) interfere with the Path Tracer's sampling.

#### Security & Safety Notes

- No credentials or sensitive configuration is required for the rendering process described here.
- Output directories may contain large sequence files. Ensure sufficient disk space before initiating a full 4K render.

#### Common Pitfalls

- **Problem:** The render output is blurry or soft despite being set to 4K.
  **Solution:** Increase Screen Percentage to 125 or 150 for Lumen renders. This renders at a higher internal resolution and downscales, producing a sharper result.
- **Problem:** Path Tracing renders are extremely noisy and render times are excessive.
  **Solution:** Test sample counts in the viewport first. Use Spatial Sample Count and Temporal Sample Count values that multiply to at least 1000 for a clean final image, and disable Screen Percentage to avoid unnecessary overhead.
- **Problem:** Only one camera renders despite multiple cameras being present in the Sequencer.
  **Solution:** Verify the Camera Cut track has keyframes for each camera at the correct frame ranges. Scrub the Camera Cut track to confirm the view switches between cameras as expected before rendering.
- **Problem:** The Camera Cut track shows the wrong camera at a given frame.
  **Solution:** Add camera entries to the Camera Cut track using the plus button. Set the correct camera actor for each frame range and extend or trim the keyframes as needed.

---

### Lesson 3: Multi-Camera Sequences and Camera Locking

#### Examples

##### Example 1: Adding a Second Camera to the Camera Cut Track

The initial Camera Cut track showed only Camera 1 from frame 0 to frame 548. By clicking the plus button on the Camera Cut track and selecting CineCameraActor2 at frame 124, the render automatically switched to Camera 2 from frame 124 to frame 548, producing a 424-frame segment from the second angle without any manual timeline edits.

##### Example 2: Verifying Camera Cut Output Before Rendering

Before rendering, the Camera Cut track can be scrubbed to verify which camera is active at each frame. Locking into the Camera Cut track view (by clicking the camera cut icon) ensures the viewport shows exactly what will be rendered, preventing accidental renders from a different camera angle.

##### Example 3: Locking Camera Transforms After Positioning

After positioning both cameras for the final sequence, right-clicking each camera and selecting Transform > Lock Actor Movement prevents accidental translation or rotation of the camera during subsequent editing. This is particularly important after rendering, when the temptation to tweak angles can overwrite carefully set compositions.

#### Step 1: Review the Camera Cut Track Before Rendering

In Sequencer, locate the Camera Cut track at the top of the timeline. Click the camera cut icon to lock the viewport to the Camera Cut perspective. Scrub through the timeline to verify the active camera switches at the correct frame ranges. This confirms exactly what the Movie Render Queue will produce.

#### Step 2: Add Additional Cameras to the Camera Cut Track

To include more than one camera in the final render, click the plus button on the Camera Cut track. Select the additional CineCameraActor from the list. The new camera entry is placed at the current timeline position. Extend or trim the camera keyframe by dragging its edges in the track to define the exact frame range for that camera angle. Repeat for as many cameras as needed.

#### Step 3: Lock Camera Transforms

Once camera positions are finalized, select each camera actor in the level. Right-click and navigate to Transform > Lock Actor Movement. This prevents the camera from being accidentally moved or rotated during further editing or rendering review. If the right-click menu does not show the Lock option (a known issue), restart the project and try again.

#### Best Practices

- ✅ Always scrub the Camera Cut track and lock the viewport to it before starting a render
- ✅ Use the plus button on the Camera Cut track to add all cameras needed for the sequence
- ✅ Extend or trim camera keyframes visually in the track rather than entering frame numbers manually
- ✅ Lock all camera transforms after final positioning to prevent accidental changes
- ✅ Restart the project if the Lock Actor Movement option is missing from the right-click menu
- ❌ Do not assume all cameras in the Sequencer will render; only the Camera Cut track cameras are rendered
- ❌ Do not skip verifying the Camera Cut track before rendering; a wrong camera at a key frame ruins the sequence
- ❌ Do not leave cameras unlocked during render review; an accidental drag can ruin hours of positioning

#### Keep In Mind

- The Camera Cut track is the authoritative source for what renders. Cameras not present in this track are ignored during Movie Render Queue output.
- Locking the viewport to the Camera Cut track icon prevents confusion about which camera is being viewed.
- Camera keyframes in the Camera Cut track can be dragged to extend or shorten each camera's active frame range.
- The Lock Actor Movement option is per-camera and persists across sessions once applied.

#### Security & Safety Notes

- No security-sensitive operations are involved in camera locking or Camera Cut track management.

#### Common Pitfalls

- **Problem:** Only Camera 1 renders despite other cameras existing in the Sequencer.
  **Solution:** Add the other cameras to the Camera Cut track using the plus button. Verify each camera has a keyframe spanning its intended frame range.
- **Problem:** Cannot find the Lock Actor Movement option when right-clicking a camera.
  **Solution:** This is a known issue in Unreal Engine. Exit and restart the project, then try right-clicking the camera again.
- **Problem:** Camera Cut track viewport shows a different angle than expected.
  **Solution:** Ensure the viewport is locked to the Camera Cut track icon (not a specific camera). Scrub the timeline to confirm the correct camera is active at each frame.

---

## Glossary / Index

|Term|Definition|
|----|----------|
|Anti-Aliasing|A rendering technique that smooths jagged edges; in Path Tracing it must be set to None and controlled via sample counts instead|
|Console Variable Preset|A saved collection of engine console variable values that can be loaded at project open to avoid re-entering commands manually|
|Custom Playback Range|Render settings that override the Sequencer frame range with a user-defined start and end frame for targeted rendering|
|EXR|A 16-bit image format that preserves maximum color information for professional post-production color grading|
|Frame Rate|The number of frames rendered per second, configurable from 12 FPS to 240 FPS or custom values in the Movie Render Queue|
|JPEG|An 8-bit image format suitable only for test renders due to color compression; not recommended for final output|
|Lumen|Unreal Engine 5's built-in real-time global illumination and reflection system; the default and fast renderer for most projects|
|Movie Render Queue|The dedicated UE5 rendering panel used to configure and execute cinematic and image sequence exports|
|Multi-Camera Sequence|A Sequencer setup with two or more CineCameraActors where the Camera Cut track switches between cameras per frame range|
|Path Tracing|A physically-based offline renderer that produces highly realistic lighting and reflections at the cost of significantly longer render times|
|PNG|A lossless image format with optional alpha channel support; the recommended format for social media and preview renders|
|Screen Percentage|A render setting that controls internal render resolution relative to output resolution; values above 100% supersample for sharper Lumen output|
|Sequencer|Unreal Engine's timeline-based cinematic editing tool used to animate cameras, actors, and effects for rendered output|
|Spatial Sample Count|The anti-aliasing sample count per pixel per frame; multiplied by Temporal Sample Count to produce total samples for Path Tracing|
|Samples Per Pixel|The number of light samples calculated per pixel; higher values reduce noise and flickering but increase render time|
|Temporal Sample Count|The anti-aliasing sample count accumulated over time (frames); multiplied by Spatial Sample Count for total Path Tracing samples|
|Temporal Super Resolution|A real-time upscaling anti-aliasing method used in the UE5 viewport that allows lower screen percentages without visible quality loss|
