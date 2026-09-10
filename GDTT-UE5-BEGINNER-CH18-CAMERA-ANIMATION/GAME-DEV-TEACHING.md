# Unreal Engine 5 Chapter 18: Camera Animation in Sequencer

## Overview

This chapter teaches how to set up shots and animate cameras in Unreal Engine 5 using Sequencer to create cinematic sequences. It covers placing cameras, keyframing camera transforms, animating focus and depth of field, using camera cut tracks for multi-angle shots, adjusting animation play rates, and modifying lighting per shot. By the end, you will be able to create professional-looking camera animations like side-scrolling tracking shots and wide establishing shots.

## When to Follow Game Dev Teachings

- When you need to set up cinematic camera shots in Unreal Engine 5 Sequencer
- When working with multiple cameras and camera cut tracks in a single sequence
- When the user asks about animating camera transforms, focus, or depth of field in UE5

## Lessons From Game Dev Teachings

### Lesson 1: Setting Up Shots and Adding Cameras to Sequencer

#### Examples

##### Example 1: Side-Scrolling Tracking Shot

Place the camera at ground level between actors, adjust focal length and wide-screen film back settings, then animate the camera's X location to side-scroll alongside the walking stormtroopers while keeping them in frame.

##### Example 2: Wide Establishing Shot Behind a Spaceship

Place a second camera behind a large set piece at a high, wide angle with a long focal length to capture the scale of the scene and the crowd of actors marching forward.

#### Step 1: Plan Your Storyboard and Shot List

Before opening Sequencer, know the shots you want in your final cinematic. Setting up cameras early in the project is crucial — build only what your cameras will see, since that is all you will render.

#### Step 2: Open or Reopen Your Sequencer

Animations disappear when Unreal Engine is closed and reopened. Open the Sequencer by either double-clicking the level sequence in the Content Drawer or right-clicking it in the Outliner. If your editor windows are misaligned, reset via Window > Load Layout > Default Editor Layout.

#### Step 3: Add a Camera to Your Scene

From the top-left menu, add an Actor to the scene via Cinematics > Cine Camera Actor. Position the camera at ground level or wherever your shot requires. Adjust the Details panel properties such as Focal Length, Aperture, and Focus Method to compose your initial frame.

#### Step 4: Add the Camera to the Sequencer

With the Sequencer open, click the Track button, select your camera actor, and add it to the sequence. A Camera Cuts track is automatically created at the top of the Sequencer timeline. This track displays a filmstrip of the current camera view and shows the active camera name.

#### Step 5: Compose and Refine the Shot

Preview the camera view by clicking the camera in the Sequencer. Use the Details panel to adjust Focal Length, Aperture, Focus, and Film Back settings. Experiment with different values — there is no single "correct" focal length. Use wide-screen ratios (e.g., Film Back sensor size of 34x14) and a Squeeze Factor of 2 for an anamorphic lens look. Fine-tune the shot until it matches your storyboard vision.

#### Best Practices

- ✅ Set up your cameras early in the project, not at the end
- ✅ Build your scene geometry only for what your camera will see to save performance
- ✅ Storyboard your shots before animating so you know the intended camera angles
- ✅ Eject the camera view (unlock) when positioning a second camera to avoid accidental movement
- ✅ Pin the Sequencer preview window so you can see changes while working from a distance

#### Keep In Mind

- When you reopen Unreal Engine, animations do not persist in the viewport — always reopen your Sequencer to restore them.
- A Camera Cuts track is automatically added when you add your first camera to the Sequencer.
- Changing one parameter (like Focal Length) often requires adjusting others (like Film Back or Squeeze Factor) to maintain your desired composition.

#### Security & Safety Notes

- This chapter focuses on cinematic setup within the Unreal Editor. No scripts, code execution, or console command automation is required for normal operation.

#### Common Pitfalls

- **Problem:** Stormtrooper shadows disappear when the camera is placed far away.
  **Solution:** Ray tracing culling is cutting shadow rays for distant objects. Use the console command `r.raytracing.culling 0` to disable culling and restore shadows.
- **Problem:** Look-at tracking snaps to the wrong body part (e.g., an actor's foot instead of their torso).
  **Solution:** Use the eyedropper tool to select the actor before enabling Look-at Tracking, then use the Relative Offset Z-axis value to shift the tracking point upward.
- **Problem:** Decals turn characters yellow when they overlap.
  **Solution:** Select the character, open the Details panel, search for "Decal," and disable "Receive Decals" on that mesh.

### Lesson 2: Animating Camera Transforms and Keyframing Movement

#### Examples

##### Example 1: Ascending Camera Reveal

Start the camera at ground level with a first keyframe. Raise the camera's Z location over time with a second keyframe. As the stormtroopers walk past and the spaceship door opens, the ascending camera reveals the door and the scene above.

##### Example 2: Side-Scrolling Camera Tracking Shot

Set two keyframes for the camera's X location. At frame 1, position the camera ahead of the stormtroopers. At a later frame, pull the camera back so it drifts alongside them. Play the sequence to verify the camera maintains the actors in frame as it moves.

#### Step 1: Zero Out and Lock Camera Transforms

Navigate to the camera's Transform values and zero them out to set a clean starting position. Hit the keyframe button for all transform properties (Location and Rotation) at frame 1. This locks the initial state of the camera.

#### Step 2: Animate Camera Location and Rotation

Scrub to a later frame, move the camera to a new position or angle, and press the keyframe button again. A new keyframe is created. Repeat for each waypoint in your camera movement. Right-click keyframes in the curve editor and set them to Linear to achieve constant-speed motion.

#### Step 3: Adjust Tracking Speed for Smooth Follow

If using Look-at Tracking, adjust the Tracking Interpolation Speed value (e.g., set to 4) to control how quickly the camera snaps to the tracked actor. Lower values create a smoother, delayed follow; higher values are more responsive.

#### Step 4: Extend the Timeline to Match Shot Length

If actors are sliding or finishing their walk too early, extend the timeline end by dragging the Sequencer range. Pull the end keyframe markers of the animation curves further back (e.g., to frame 500) so the walking animation lasts long enough for the entire camera move.

#### Step 5: Fine-Tune Camera Start Timing

Pull the first camera keyframe back on the timeline so the camera is already in motion by the time the shot opens. This avoids a static start and creates a more dynamic feel from the first frame.

#### Best Practices

- ✅ Keyframe all transform channels (Location and Rotation) at each waypoint
- ✅ Use Linear interpolation for constant-speed tracking shots
- ✅ Extend the animation timeline to match the duration of the longest animated element
- ✅ Pull back the first camera keyframe so the shot starts in motion

#### Keep In Mind

- If your camera starts slow and then accelerates unexpectedly, pull the first keyframe earlier on the timeline so the motion is already established before the shot opens.
- Keyframing a property while another property is selected will only keyframe the selected property — make sure to select all transforms before hitting the keyframe button if you want to lock them all.

#### Security & Safety Notes

- Normal Sequencer keyframing poses no security risk. Avoid running untrusted console commands or scripts from external sources.

#### Common Pitfalls

- **Problem:** Camera movement starts slow and then suddenly speeds up.
  **Solution:** Pull the first camera keyframe back in the timeline so the movement begins before the shot starts.
- **Problem:** Camera is tracking the wrong part of an actor (e.g., foot instead of torso).
  **Solution:** Use the eyedropper tool to select the correct actor before enabling Look-at Tracking, then use Relative Offset Z-axis to raise the tracking point.
- **Problem:** Shadows are missing on distant actors.
  **Solution:** Apply the console command `r.raytracing.culling 0` to disable ray tracing distance culling.

### Lesson 3: Animation Timing, Focus, and Depth of Field

#### Examples

##### Example 1: Slow-Motion Spaceship Door Opening

Right-click the spaceship door's animation layer in the Sequencer, open Properties, and set Play Rate to 0.5 to double the effective duration of the door opening animation. This gives the camera more time to capture the action without rushing.

##### Example 2: Animated Focus Pull from Stormtroopers to Spaceship

Enable Debug Focus Plane and position it on the stormtroopers. Set a low Aperture value for a blurry background. Keyframe the Focus Distance at the first frame, then scrub forward and change the focus to the spaceship and keyframe again. Play the shot to see the focus pull transition in real time.

#### Step 1: Adjust Animation Speed with Play Rate

Right-click an animation layer in the Sequencer, select Properties, and modify the Play Rate. A value of 0.5 plays the animation at half speed (slower), while 2.0 plays it at double speed (faster). This is useful for slowing down fast actions to give your camera more time to frame the shot.

#### Step 2: Enable Focus Debugging

Select the camera in the scene, open the Details panel, and enable Debug Focus Plane. This draws a visual plane in the viewport showing exactly where the camera's current focus is set. Use this to position the focus precisely on your subject.

#### Step 3: Adjust Depth of Field with Aperture

Lower the Aperture value to increase background blur (shallow depth of field). Higher Aperture values keep more of the scene in focus. Combine with a high Focal Length for a compressed, cinematic look with a blurred background.

#### Step 4: Animate Focus Distance Over Time

Scrub to the first frame where you want the focus to start, set the Focus Distance, and press the keyframe button. Scrub forward to the point where you want the focus to shift, adjust the Focus Distance, and keyframe again. Repeat as needed to create focus pull transitions during the shot.

#### Step 5: Close the Debug Focus Plane

Once the focus is set correctly, disable Debug Focus Plane in the camera's Details panel. Preview the shot to confirm the bokeh and focus behavior look natural without the debug overlay.

#### Best Practices

- ✅ Use Play Rate to slow down fast animations and give your camera more time to compose the shot
- ✅ Use Debug Focus Plane to visually verify where your focus is before finalizing
- ✅ Lower Aperture for cinematic bokeh; raise it for everything-in-focus shots
- ✅ Animate Focus Distance to create dynamic focus pulls that guide audience attention

#### Keep In Mind

- Play Rate affects the entire animation layer — if you slow down the door animation, all keyframes within that layer play back at half speed.
- If Focus Distance is not visible in the camera's Details panel, click the + (plus) icon on the camera component to expand all available trackable properties.

#### Security & Safety Notes

- Adjusting Play Rate, Aperture, and Focus Distance are safe editor operations with no security implications.

#### Common Pitfalls

- **Problem:** Animation plays too fast and the camera cannot keep up.
  **Solution:** Right-click the animation layer, open Properties, and set Play Rate to 0.5 or lower to slow it down.
- **Problem:** Cannot find the Focus Distance property to keyframe.
  **Solution:** Click the + (plus) icon on the camera component in the Sequencer to expand all available camera tracks, then add Focus Distance to the track list.
- **Problem:** Background is too blurry or not blurry enough.
  **Solution:** Adjust the Aperture value in the camera's Details panel. Lower values increase blur; higher values reduce it.

### Lesson 4: Multi-Camera Cuts, Lighting Per Shot, and Performance Fixes

#### Examples

##### Example 1: Camera Cut Between Wide Establishing Shot and Side-Scrolling Shot

Add a second Cine Camera Actor to the scene. Position it for a wide, behind-the-spaceship angle. In the Sequencer, add this second camera to a new slot on the Camera Cuts track. Scrub across the Camera Cuts track and assign each camera to the desired time range. When rendered, the sequence will automatically switch between cameras.

##### Example 2: Per-Shot Lighting Adjustments

After setting up a new camera angle, adjust the scene lighting to match the mood of that specific shot. Move lights, change intensities, or reposition them so the subject pops against the background. Different shots almost always require different lighting setups — there is no one-size-fits-all lighting rig.

#### Step 1: Add a Second Camera to the Scene

Drag in a new Cine Camera Actor from Cinematics. Position and compose it for a different angle. Adjust its Focal Length, Film Back, and Aperture to match the desired look for this second shot.

#### Step 2: Set Up Look-at Tracking

Select the second camera. Before enabling Look-at Tracking, use the eyedropper tool in the Details panel to select the target actor. Then enable Look-at Tracking. If the camera tracks the wrong part of the actor, use the Relative Offset Z-axis value to lift the tracking point above the ground and center it on the actor's torso.

#### Step 3: Keyframe the Second Camera's Transforms

On the first frame, zero out and keyframe all transform values for the second camera. Scrub to a later frame, reposition the camera to the end of its move, and keyframe again. Set keyframe interpolation to Linear for constant-speed motion. Adjust the Tracking Interpolation Speed (e.g., 4) for a smooth, delayed follow.

#### Step 4: Configure Camera Cuts

With both cameras added to the Sequencer, the Camera Cuts track at the top of the timeline now has slots for each camera. Assign Camera Actor 1 to the first time range and Camera Actor 2 to the second time range. When you play or render, Unreal Engine will automatically switch between the cameras at the specified times.

#### Step 5: Fix Ray Tracing Shadow Culling

If shadows disappear on actors when the camera is far away, this is caused by ray tracing culling (a performance optimization that drops shadow rays for distant objects). Open the Unreal Engine console and enter `r.raytracing.culling 0` to disable this behavior. Note: this issue only affects Lumen ray tracing — path tracing does not have this problem.

#### Step 6: Fix Decal Artifacts on Characters

If decals cause characters to appear with yellow or discolored patches, select each affected character in the scene. In the Details panel, search for "Decal" and disable the "Receive Decals" option on the character mesh. This prevents decal projection from affecting the character material.

#### Step 7: Adjust Per-Shot Lighting

After setting up each new camera angle, spend time adjusting the lighting. Move lights, change intensities and colors, and reposition them to match the mood of the specific shot. Lighting changes per shot are normal and expected — even in real productions, lights are repositioned between every angle.

#### Best Practices

- ✅ Use the eyedropper tool to select the tracking target before enabling Look-at Tracking
- ✅ Use Relative Offset Z-axis to fine-tune the tracking height
- ✅ Set Tracking Interpolation Speed to 4 or higher for smooth actor following
- ✅ Disable `r.raytracing.culling` when using wide shots with distant objects under Lumen
- ✅ Disable "Receive Decals" on characters that are being discolored by overlapping decals
- ✅ Adjust lighting for every new shot — one lighting setup does not work for every camera angle

#### Keep In Mind

- The Camera Cuts track is created automatically when the first camera is added to the Sequencer.
- Look-at Tracking snaps to a random location if the eyedropper tool is not used first to select the target actor.
- Path tracing does not suffer from ray tracing culling, so if you use path tracing for renders, you will not need the `r.raytracing.culling 0` console command.
- Stormtroopers (or any character) may appear to slide if their walk animation is too short for the camera move — always extend the timeline and pull back the animation end keyframes to match.

#### Security & Safety Notes

- The console command `r.raytracing.culling 0` is a safe editor setting for cinematic work. It disables a GPU optimization; it does not execute code or modify files.
- Do not paste or run arbitrary console commands or scripts from untrusted sources.

#### Common Pitfalls

- **Problem:** Stormtrooper shadows disappear when the camera is far away.
  **Solution:** Enter `r.raytracing.culling 0` in the Unreal Engine console to disable Lumen ray tracing distance culling.
- **Problem:** Characters slide unnaturally through the scene.
  **Solution:** Extend the Sequencer timeline and pull the animation end keyframes back to frame 500 or later to give characters enough time to complete their walk.
- **Problem:** Decals cause characters to turn yellow or show discoloration.
  **Solution:** Select each character, search for "Decal" in the Details panel, and disable "Receive Decals."
- **Problem:** Look-at Tracking snaps to a random position.
  **Solution:** Use the eyedropper tool to select the target actor before enabling Look-at Tracking.

## Glossary / Index

|Term|Definition|Page(s)|
|----|----------|-------|
|Anamorphic Lens Effect|A widescreen cinematic look achieved by setting the film back Squeeze Factor to 2, stretching the image horizontally|11–12|
|Aperture|Camera setting controlling depth of field; lower values increase background blur|9, 26, 29|
|Camera Cuts Track|A Sequencer track that manages multiple cameras and their time ranges, automatically added when the first camera is added to a sequence|18–20|
|Camera Transform|The Location and Rotation properties of a camera actor, keyframed to create camera movement|12, 21–23|
|Cine Camera Actor|A specialized Unreal Engine 5 actor designed for cinematic camera work with adjustable film back, focal length, and aperture|5, 19, 30|
|Debug Focus Plane|A camera debug setting that renders a visual plane in the viewport showing the current focus distance|9, 27|
|Decal|A projected texture applied to surfaces in the scene; can cause visual artifacts on character meshes|29–30|
|Details Panel|The right-side inspector panel in Unreal Engine showing editable properties for the selected actor or asset|6, 9, 13, 27, 30|
|Eject|A viewport action that unlocks the camera view, returning control to the default perspective camera|9, 19, 23|
|Focal Length|Determines the camera's field of view; higher values zoom in, lower values zoom out (wide angle)|6–7, 13, 24–26|
|Focus Distance|The distance from the camera at which objects are in sharp focus; animatable for focus pull effects|9–10, 27–29|
|Interpolation Speed|Controls how smoothly the camera follows a tracked actor; lower values produce smoother, delayed tracking|23, 32|
|Keyframe|A marker in the Sequencer timeline that records a property value (e.g., camera location) at a specific frame|8, 12, 21–23|
|Linear Interpolation|A keyframe interpolation mode that produces constant-speed motion between two points|23, 32|
|Lumen|Unreal Engine 5's global illumination system; affected by ray tracing culling when cameras are far from objects|21, 33|
|Play Rate|A property on an animation layer that scales animation playback speed (e.g., 0.5 = half speed, 2.0 = double speed)|11–12, 28|
|Ray Tracing Culling|A GPU performance optimization in Lumen that disables shadow rays for distant objects; causes missing shadows when the camera is far away|21, 33|
|Receive Decals|A mesh property that controls whether decals are projected onto a character; should be disabled when decals cause visual artifacts|29–30|
|Relative Offset|A setting on Look-at Tracking that offsets the tracked point along an axis (e.g., Z-axis) to adjust where on the actor the camera looks|23, 31–32|
|Sequencer|Unreal Engine 5's timeline-based cinematic editor for animating actors, cameras, and properties|5, 17, 20, 23|
|Tracking Interpolation Speed|Controls the responsiveness of Look-at Tracking; set to 0 for instant snap or higher values for smooth delayed follow|23, 32|
|Track Icon|The plus (+) icon in the Sequencer used to add new property tracks (e.g., Focus Distance, Aperture) to a selected actor|9, 28|
