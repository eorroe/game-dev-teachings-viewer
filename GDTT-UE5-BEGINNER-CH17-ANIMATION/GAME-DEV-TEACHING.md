# UE5 Beginner Chapter 17: Animation

## Overview

This chapter introduces animation in Unreal Engine 5 using the Sequencer, covering keyframing, graph editing, and calling existing skeletal animations. It teaches how to bring objects to life in a cinematic scene by animating transforms and controlling motion curves.

## When to Follow Game Dev Teachings

- When you need to add movement to actors in a cinematic sequence
- When working with Sequencer for the first time
- When the user asks how to animate props, doors, or simple objects in UE5

## Lessons From Game Dev Teachings

### Lesson 1: Sequencer Basics and Adding Actors

#### Examples

##### Example 1: Adding a Sphere to Animate a Droid-like Object

A simple sphere is added to the scene and brought into the Sequencer to practice basic movement keyframing before moving to complex skeletal meshes.

##### Example 2: Calling an Existing Skeletal Animation

The spaceship door already contains an animation sequence; the lesson shows how to add the skeletal mesh to Sequencer and use its existing animation track rather than creating motion from scratch.

#### Step 1: Create a Level Sequence

Go to the top-left dropdown and choose Add Level Sequence. Save it in a dedicated Sequencer folder inside the Content drawer so each cinematic event has its own timeline.

#### Step 2: Add Actors to the Sequencer

Use the Track button then Actor To Sequencer, or drag and drop the actor from the Outliner directly into the Sequencer panel. The selected actor appears with its transform tracks.

#### Step 3: Understand the Sequencer Layout

The Sequencer has three parts: settings dropdowns at the top, the actor list on the left, and animation tracks on the right. The plus icons beside each property allow adding additional tracks as needed.

#### Step 4: Set the Timeline Length

The default timeline is 150 frames at 30 FPS, which equals 5 seconds. Drag the red end marker to extend or shorten the animation duration.

#### Step 5: Return to Frame Zero

Use the first-frame button or type 0 in the frame field to ensure the first keyframe is placed at the start of the timeline.

#### Best Practices

- ✅ Create a dedicated Sequencer folder for each Level Sequence
- ✅ Use drag and drop from the Outliner for fast actor addition
- ✅ Keep the timeline short while learning; extend it once the shot is clear
- ❌ Don’t forget to save the Level Sequence before closing the editor

#### Keep In Mind

- Objects in UE5 are referred to as actors inside Sequencer.
- The Sequencer is the UE5 equivalent of a timeline in DaVinci Resolve or Premiere.

#### Security & Safety Notes

- No security-sensitive operations are involved in this lesson.

#### Common Pitfalls

- **Problem:** Deleting an actor from the scene while it is selected in Sequencer triggers a confusing confirmation prompt.
  **Solution:** Delete actors from the Sequencer panel instead of the viewport to avoid accidental removal.

### Lesson 2: Keyframing Transforms and Animating Motion

#### Examples

##### Example 1: Rolling Sphere from TIE Fighters to Spaceship

A sphere is keyframed to travel from the left side of the scene to the spaceship door, creating a droid-like roll effect.

##### Example 2: Scaling the Sphere While It Moves

Scale keyframes are added so the sphere starts small and grows as it reaches the destination, adding visual personality to the motion.

#### Step 1: Keyframe the Start Position

Select the actor in Sequencer, scrub to frame 0, position the object in the viewport, and click the keyframe button beside Location to record the starting transform.

#### Step 2: Move the Object and Keyframe the End

Scrub to the final frame, move the actor to its destination, and the Sequencer automatically creates a second keyframe when auto-key is active or when manually confirming the change.

#### Step 3: Preview the Animation

Press Space to play the timeline and watch the object travel between the two keyframes. The motion path is visualized as a line connecting the keyframes.

#### Step 4: Animate Scale

Scrub to the desired frame, change the Scale value, and click the keyframe button beside Scale. Use the arrow buttons beside keyframes to jump precisely between them.

#### Step 5: Use Graph Editor for Precision

Click the Graph button to open the curve editor. Expand the transform channels to see the motion curves, normalize the view if the values are too large to fit, and drag the curve handles to fine-tune the motion.

#### Best Practices

- ✅ Use the Sequencer’s built-in sliders when possible; they auto-create keyframes
- ✅ Use the arrow buttons next to keyframes to jump between exact keyframe times
- ✅ Open the graph editor when you need precise control over speed and easing
- ❌ Don’t rely solely on dragging in the viewport without confirming keyframes

#### Keep In Mind

- The Enter key can also create keyframes when the timeline is active.
- Ctrl+Z undoes keyframe changes; Ctrl+Y redoes them.

#### Security & Safety Notes

- No security-sensitive operations are involved in this lesson.

#### Common Pitfalls

- **Problem:** The sphere jumps back to its original position after undoing.
  **Solution:** Re-enter the keyframe after undoing, because Undo does not always preserve keyframe state.
- **Problem:** Graph curves look flat even though the object is moving.
  **Solution:** Expand the correct transform channel in the graph; Rotation often shows flat lines when only Location is animated.

### Lesson 3: Graph Editor, Tangents, and Animation Speed

#### Examples

##### Example 1: Slow-Start, Fast-Middle, Slow-End Motion

By adjusting weighted tangents on the location curve, the sphere accelerates quickly and decelerates smoothly at the end.

##### Example 2: Overshoot Scale Effect

Scale tangents are shaped so the sphere starts oversized, shrinks while moving, and creates a dynamic overshoot feel.

#### Step 1: Open the Graph Editor

Select the actor in Sequencer and click the Graph button. Expand Transform to see Location, Rotation, and Scale sub-channels.

#### Step 2: Identify Active Channels

Flat lines mean no animation exists on that channel. Active motion appears as sloped curves. In the lesson, only X location and scale show curves because movement is primarily along one axis.

#### Step 3: Normalize the Graph View

If keyframe values are too large to compare visually, click the Normalize View button to compress values between 0 and 1 for easier editing.

#### Step 4: Adjust Keyframe Position

Drag keyframes left or right on the graph to change timing, or drag them up and down to change the property value at that exact frame.

#### Step 5: Change Tangent Types

Select keyframes, click the tangent arrow icon, and switch to Weighted Tangents. Drag the tangent handles to control acceleration and deceleration exactly like shaping a camera rail curve.

#### Step 6: Preview and Refine

Press Space to preview the animation. Use G to toggle viewport overlays for a cleaner preview. Return to the graph and adjust tangents until the motion feels intentional.

#### Step 7: Save and Exit the Graph

Click Save and close the graph editor when satisfied. The Sequencer retains all keyframe data.

#### Best Practices

- ✅ Use weighted tangents for full control over motion curves
- ✅ Normalize the graph view when comparing start and end values
- ✅ Preview frequently while editing curves
- ❌ Don’t leave the graph editor without saving changes

#### Keep In Mind

- Weighted tangents in UE5 behave similarly to camera rig rail handles.
- The graph editor is powerful but not required for simple linear motion.

#### Security & Safety Notes

- No security-sensitive operations are involved in this lesson.

#### Common Pitfalls

- **Problem:** The object moves in the wrong direction or axis.
  **Solution:** Check the Location X, Y, and Z channels individually; only the active axis will show a sloped curve.
- **Problem:** Animation feels stiff or robotic.
  **Solution:** Adjust tangent handles to add ease-in and ease-out; avoid leaving tangents in the default linear mode.

### Lesson 4: Calling Existing Skeletal Animations

#### Examples

##### Example 1: Spaceship Door Opening Animation

The spaceship is a skeletal mesh that already contains an animation sequence. The lesson demonstrates adding the spaceship to Sequencer and activating its existing door-opening animation without rebuilding it.

##### Example 2: Animating Stormtrooper Walk Cycles

Stormtroopers use Mixamo animations. Once imported, they appear as animation tracks in Sequencer and can be triggered like any other clip.

#### Step 1: Add the Skeletal Mesh to Sequencer

Select the spaceship, click Actor To Sequencer, and confirm it appears in the Sequencer with an Animation track above Transform.

#### Step 2: Identify the Existing Animation Track

Because the spaceship is a skeletal mesh with an armature, it automatically includes animation tracks for any animation sequences stored with the asset.

#### Step 3: Activate the Animation

Expand the Animation track and set the desired animation sequence to play. Adjust the start frame and length to match the cinematic timing.

#### Step 4: Sync Multiple Animations

Coordinate the door animation with camera movement and walk cycles by aligning their start frames and extending the timeline as needed.

#### Best Practices

- ✅ Reuse existing skeletal animations instead of rebuilding them
- ✅ Organize animation sequences in dedicated folders
- ✅ Sync animation start times visually in the Sequencer timeline
- ❌ Don’t create duplicate animation tracks for the same mesh

#### Keep In Mind

- Skeletal meshes automatically include animation tracks in Sequencer.
- Static meshes do not have animation tracks unless explicitly added.

#### Security & Safety Notes

- No security-sensitive operations are involved in this lesson.

#### Common Pitfalls

- **Problem:** The animation track is missing after adding a skeletal mesh.
  **Solution:** Ensure the mesh was imported with its animation sequence and skeleton properly assigned.
- **Problem:** Console variables reset after reopening UE5.
  **Solution:** Save console commands as presets in Window > Console Variables and reload them on project open.

## Glossary / Index

|Term|Definition|
|----|----------|
|Actor|Any object placed in a UE5 level, including meshes, lights, and cameras; actors can be added to Sequencer for animation|
|Animation Layer|A track in Sequencer that controls animation playback properties such as Play Rate|
|Animation Sequence|A baked motion asset for a skeletal mesh that can be assigned and played inside Sequencer|
|Auto-Key|A Sequencer mode that automatically creates keyframes when a property changes on the timeline|
|Curve Editor|A graph view inside Sequencer that displays and edits animation curves for precise motion control|
|Ease In / Ease Out|Acceleration and deceleration behavior controlled by tangent handles on animation curves|
|Frame|The smallest time unit in Sequencer; 30 frames equal one second at 30 FPS|
|Graph Editor|The Sequencer panel used to visualize and fine-tune animation curves and tangent handles|
|Keyframe|A recorded snapshot of an object’s property values at a specific frame|
|Level Sequence|A standalone Sequencer asset saved in the Content drawer that contains all timeline data for a cinematic event|
|Location|The X, Y, Z position of an actor; one of the three core transform properties animated in Sequencer|
|Normalized View|A graph editor display mode that compresses value ranges between 0 and 1 for easier curve comparison|
|Play Rate|A property on an animation layer that scales playback speed, where 1.0 is normal speed and 0.5 is half speed|
|Rotation|The pitch, yaw, and roll orientation of an actor; animated when objects need to turn during motion|
|Scale|The size multiplier of an actor along each axis; animated for growth, shrink, or squash-and-stretch effects|
|Sequencer|UE5’s timeline-based editor for animating actors, cameras, properties, and effects for cinematic output|
|Skeletal Mesh|A mesh with an armature/bone structure that can play animation sequences and expose animation tracks in Sequencer|
|Tangent Handle|A control point on a graph curve that shapes acceleration and deceleration between keyframes|
|Timeline|The horizontal time ruler in Sequencer that displays frames, playhead position, and animation duration|
|Track|A row in Sequencer representing one animatable property or channel, such as Location, Rotation, Scale, or Animation|
|Transform|The combined Location, Rotation, and Scale properties of an actor|
|Weighted Tangents|A tangent mode in the graph editor that gives full control over curve shape for custom motion profiles|
