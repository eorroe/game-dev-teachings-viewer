# UE5 Beginner Chapter 16: Cameras

## Overview

This game dev teaching covers cameras in Unreal Engine 5, teaching how to add Cine Camera Actors to scenes, configure camera settings, and use camera rigs for cinematic shots. It explains how to apply real-world camera concepts like focal length, aperture, depth of field, and focus tracking within UE5's viewport and details panel. These skills are essential for creating cinematic sequences, previewing shots early, and avoiding wasted work by locking in camera angles before building world detail.

## When to Follow Game Dev Teachings

- When you need to set up cinematics or gameplay camera angles in Unreal Engine 5
- When working with depth of field, bokeh, focus tracking, or anamorphic-style effects
- When the user asks how to move cameras along a path using camera rig rails or cranes
- When previewing camera shots before committing to final scene geometry and lighting

## Lessons From Game Dev Teachings

### Lesson 1: Adding and Previewing a Cine Camera Actor

#### Examples

##### Example 1: Adding a Camera for a Cinematic Shot

Place a Cine Camera Actor into the scene via the Cinematic category or the Place Actors panel. Once placed, select it and use the viewport preview at the bottom right to frame your shot.

##### Example 2: Switching Between Multiple Camera Views

Duplicate the Cine Camera Actor using Alt+drag to create multiple cameras at different positions. Switch between them using the Perspective dropdown at the top left, where Cine Camera Actor entries appear under Place Cameras.

#### Step 1: Add a Cine Camera Actor

Open the Place Actors panel or go to Cinematic in the Add menu and drag a Cine Camera Actor into the level. This is the standard camera type used for cinematics in UE5, as opposed to the generic Camera Actor used for gameplay purposes.

#### Step 2: Position the Camera

Use the viewport Gizmo to move and rotate the camera. Press F while the camera is selected to focus the viewport on it. Use the on-screen mesh at the camera to visualize its orientation.

#### Step 3: Preview the Camera Feed

With the camera selected, observe the preview window at the bottom right of the viewport. This shows exactly what the camera sees, including depth of field and any bokeh effects.

#### Step 4: Pin the Preview

Click the pin button at the bottom left of the preview window to keep the camera preview visible while selecting and moving other actors. This is useful for framing shots while repositioning props or characters. Note that each pinned preview renders an additional viewport angle, which may reduce FPS.

#### Step 5: Pilot the Camera

Right-click the camera and select Pilot Cine Camera Actor to enter the camera's view directly. You will see black bars indicating the camera's current aspect ratio. Navigate the viewport as normal while inside pilot mode. Press E or click the eject button on the right side of the viewport to exit pilot mode.

#### Step 6: Switch Cameras via Perspective Dropdown

When Cine Camera Actors exist in the level, they appear under Place Cameras in the Perspective dropdown at the top left of the viewport. Selecting one enters pilot mode for that camera. This is often faster than right-clicking and is the preferred method for many users.

#### Best Practices

- ✅ Set your cameras and post-process volumes early in production to avoid building unnecessary world detail
- ✅ Use the Perspective dropdown or right-click pilot to enter camera view
- ✅ Use the pin button when repositioning multiple actors while keeping a camera preview visible
- ✅ Keep camera pilot mode visual indicators on to avoid confusion about which view is active

#### Keep In Mind

- Each active camera preview renders an additional scene from a different angle, so multiple pinned previews will impact performance.
- Black bars in pilot mode reflect the camera's current sensor aspect ratio; disabling the pilot visual toggle removes the bars but keeps you in pilot mode.

#### Security & Safety Notes

- Camera preview rendering has no security implications, but be aware that pinned previews consume GPU resources that could affect frame rate on lower-end hardware.

#### Common Pitfalls

- **Problem:** The camera preview disappears when selecting another actor.
  **Solution:** Click the pin button on the preview window to keep it visible while selecting other objects.
- **Problem:** The viewport shows normal perspective navigation instead of the camera view after exiting pilot mode.
  **Solution:** Re-enter pilot mode via right-click or the Perspective dropdown to verify you are inside the camera again.
- **Problem:** Multiple pinned camera previews cause severe FPS drops.
  **Solution:** Limit active pinned previews to one or two, or disable them during heavy scene editing.

### Lesson 2: Configuring Camera Settings

#### Examples

##### Example 1: Matching a Real-World Lens Look

Set the Filmback to 16:9 Digital Film, choose a focal length of 50mm, and set aperture to f/1.2 for a shallow depth-of-field portrait-style look with strong bokeh on background emissive lights.

##### Example 2: Emulating an Anamorphic Lens

Increase the Squeeze Factor to 2, adjust the sensor aspect ratio to a wider value like 2.35:1, and combine with low aperture to approximate anamorphic bokeh and edge characteristics seen in films like The Batman.

#### Step 1: Open the Camera Details Panel

Select the Cine Camera Actor and open the Details panel. The camera settings are organized into sections including Filmback, Lens Settings, Focus Settings, and Look At Tracking Settings.

#### Step 2: Configure Filmback (Sensor Settings)

Filmback represents the physical camera sensor. Use presets such as 16:9 Digital Film or IMAX 70mm, or define custom Sensor Width and Sensor Height values. Wider aspect ratios can be created by increasing the width relative to height. Note that these values are based on real-world camera specifications.

#### Step 3: Set Lens Settings

- **Focal Length:** Controls the field of view. Lower values (e.g., 24mm) create a wide-angle look; higher values (e.g., 85mm+) compress the image and are used for portraits.
- **Aperture (F-stop):** Controls depth of field. Lower numbers (e.g., f/1.2) produce more background blur and stronger bokeh; higher numbers increase overall sharpness.
- **Lens Preset:** Use Universal Zoom for full manual control. Prime lens presets lock focal length but set realistic aperture values for a specific lens.

#### Step 4: Adjust Focus Settings

Set Focus Method to Manual. Use the Focus Distance slider to set where the camera is sharpest. Enable Debug Focus Plane to visualize the focus plane in the scene. For interactive focusing, use the eye dropper tool to click on an actor and set focus distance automatically.

#### Step 5: Enable Focus Tracking

To have focus follow a moving object, set Focus Method to Tracking and use the eye dropper or search field to select the target actor. This keeps the focus plane locked to the tracked object as the camera moves.

#### Step 6: Configure Look At Tracking

Enable Look At Tracking in the Look At Tracking Settings section. Assign an Actor to Track so the camera rotates to face that object. This is useful for tracking a subject while the camera moves along a path.

#### Step 7: Apply Anamorphic Squeeze Factor

Set the Squeeze Factor to 2 to emulate anamorphic lenses. This changes the shape of bokeh highlights from circular to oval and contributes to the characteristic anamorphic look. Combine with a wider filmback aspect ratio and post-process chromatic aberration or edge blur for a more complete effect.

#### Best Practices

- ✅ Use Filmback presets based on real camera sensors for physically accurate results
- ✅ Use the eye dropper for focus and tracking targets instead of manually typing names
- ✅ Start with Universal Zoom for full control over focal length and aperture
- ✅ Enable Debug Focus Plane when manually setting focus distance to verify placement

#### Keep In Mind

- UE5 cameras replicate real-world camera behavior, making it possible to translate real photography or filmmaking knowledge directly into the engine.
- Lower aperture values increase background blur but also affect overall exposure, which may require post-process adjustments.
- Anamorphic squeeze factor alone does not perfectly replicate real anamorphic lenses; post-process effects are still needed for a full look.

#### Security & Safety Notes

- No security concerns are associated with camera settings.

#### Common Pitfalls

- **Problem:** Stormtroopers or subjects are out of focus despite setting a focus distance.
  **Solution:** Enable Debug Focus Plane to see where the focus plane is located, then adjust the Focus Distance slider until the plane intersects the desired subject.
- **Problem:** Camera tracking or focus tracking does not follow the intended actor.
  **Solution:** Ensure Look At Tracking is enabled and that the correct actor is assigned in the Actor to Track field. Use the eye dropper to avoid naming errors.
- **Problem:** Bokeh highlights appear circular when an anamorphic look is desired.
  **Solution:** Increase the Squeeze Factor to 2 and use a wider filmback aspect ratio. Oval bokeh is a signature of anamorphic lenses.

### Lesson 3: Moving Cameras with Rig Rails and Cranes

#### Examples

##### Example 1: Creating a Dolly Shot with a Camera Rig Rail

Add a Camera Rig Rail, shape it into a U-shaped curve using Bezier handles, attach the Cine Camera Actor as a child, reset its location, and animate the Current Position on Rail to move the camera along the path.

##### Example 2: Tracking a Moving Subject Along a Rail Path

Parent the camera to a Camera Rig Rail, enable Look At Tracking on the camera, assign a small hidden sphere named Tracker to the Actor to Track field, and set Focus Method to Tracking with the same tracker as the target. Animate the rail position and the camera will follow the path while keeping the tracker in focus and on screen.

#### Step 1: Add a Camera Rig Rail

Go to Cinematic in the Add menu and add a Camera Rig Rail to the scene. This actor creates a spline-based path that a camera can follow.

#### Step 2: Shape the Rail Path

Select the Camera Rig Rail and click the white dot to start the spline. Drag the Gizmo to add points. Hold Alt and drag to extend the curve and create additional points. Click a point to reveal Bezier handles and adjust the curve shape by moving or rotating the handles. Avoid placing points below ground level.

#### Step 3: Attach the Camera to the Rail

In the World Outliner, drag the Cine Camera Actor and drop it under the Camera Rig Rail to make it a child actor. With the camera selected, reset its Location and Rotation values so it snaps to the rail's origin point.

#### Step 4: Move the Camera Along the Rail

Select the Camera Rig Rail and adjust Current Position on Rail in the Details panel. Values from 0 to 1 move the camera from the start to the end of the spline. The camera follows the path smoothly.

#### Step 5: Add Tracking to the Camera Motion

Enable Look At Tracking on the camera and assign a target actor. Use a small sphere placed near the subject as a tracker if there are multiple similar actors. Name it Tracker for easy identification. Enable Focus Method to Tracking and assign the same tracker to keep the subject in focus throughout the rail movement.

#### Step 6: Use a Camera Rig Crane

Add a Camera Rig Crane from the Cinematic category. Make the camera a child of the crane instead of the rail. Reset the camera's Location and Rotation. Crane parameters include Pitch, Yaw, and Arm Length, which allow vertical and rotational movement of the camera relative to the crane base.

#### Step 7: Animate Crane and Rail Parameters

Adjust Pitch, Yaw, and Arm Length on the Camera Rig Crane to position the camera. Combine with a Camera Rig Rail for complex, curved crane shots. All of these parameters are animated in Sequencer in the following chapter.

#### Best Practices

- ✅ Shape the rail using Bezier handles for smooth camera motion rather than straight linear segments
- ✅ Reset camera Location and Rotation after parenting to a rig to ensure correct alignment with the rig origin
- ✅ Use a small dedicated tracker actor when tracking among many identical objects to avoid confusion
- ✅ Hide or disable the tracker actor after assigning it; the camera will continue tracking it

#### Keep In Mind

- Camera Rig Rails work like Bezier curves; the rail path can be edited at any time by selecting points and moving handles.
- The camera must be a child of the rail or crane for it to follow the path.
- Current Position on Rail is normalized from 0 to 1 along the entire spline length.
- Crane arm length, pitch, and yaw are relative to the crane base actor's transform.

#### Security & Safety Notes

- No security concerns are associated with rig rail or crane usage.

#### Common Pitfalls

- **Problem:** The camera does not follow the rail after parenting.
  **Solution:** Reset the camera's Location and Rotation values in the Details panel after making it a child of the rail.
- **Problem:** The camera rotates unpredictably when Look At Tracking is enabled without a valid target.
  **Solution:** Assign a specific actor to the Actor to Track field. If multiple identical actors exist, create a dedicated tracker actor and assign that instead.
- **Problem:** Focus slips out of place while the camera moves along the rail.
  **Solution:** Set Focus Method to Tracking and assign the same tracker actor used for Look At Tracking to the tracking focus target.
- **Problem:** Bezier handles do not appear when editing the rail.
  **Solution:** Click directly on a spline point in the viewport to select it; handles appear only when a point is actively selected.

## Glossary / Index

| Term | Definition | Pages in Transcript |
|------|-----------|---------------------|
| Aperture | The f-stop setting that controls depth of field and bokeh intensity; lower values produce more background blur. | 528-615, 738-756 |
| Anamorphic Lens | A type of lens that compresses the image horizontally, creating oval bokeh and characteristic edge blur; emulated in UE5 using Squeeze Factor. | 758-837 |
| Bokeh | The visual quality of out-of-focus light highlights in a shot, affected by aperture and lens type. | 718-733 |
| Camera Rig Crane | A cinematic actor that allows cameras to be raised, rotated, and extended via Pitch, Yaw, and Arm Length parameters. | 1246-1318 |
| Camera Rig Rail | A spline-based path actor that a camera can follow; shaped like a Bezier curve for smooth dolly movements. | 904-1071 |
| Cine Camera Actor | The primary camera actor used for cinematics in UE5, containing all camera sensor, lens, focus, and tracking settings. | 136-156 |
| Depth of Field | The range of distance in a shot that appears acceptably sharp, controlled primarily by aperture. | 252-256, 538-540, 602-607 |
| Filmback | The camera sensor settings, including Sensor Width and Sensor Height, that define the aspect ratio and framing of the shot. | 462-519 |
| Focal Length | The lens setting that controls field of view; lower values are wide angle, higher values are telephoto. | 528-564 |
| Focus Distance | The distance from the camera at which objects appear sharp; manually adjusted or tracked. | 626-657 |
| Focus Method | The setting that determines how focus is calculated, either Manual or Tracking. | 627-629, 1210-1212 |
| Look At Tracking | A camera setting that forces the camera to rotate and face a specified actor during movement. | 452-460, 1094-1106 |
| Pilot Mode | The viewport state where the user sees directly through the camera, including depth of field and aspect ratio bars. | 218-301 |
| Pin Preview | The ability to keep a camera's preview window visible while selecting and moving other actors in the viewport. | 388-421 |
| Squeeze Factor | A setting on the Cine Camera Actor that emulates anamorphic lens compression, changing bokeh shape from circular to oval. | 758-837 |
| Tracker | A small, often hidden actor assigned as a tracking target for camera look-at and focus tracking. | 1126-1146, 1176-1241 |
| Universal Zoom | A lens preset that allows full manual control over both focal length and aperture without locking either value. | 523-524, 566-595 |
