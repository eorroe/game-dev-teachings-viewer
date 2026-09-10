# GDTT-UE5-BEGINNER-CH5-LIGHTING: Lighting Fundamentals in Unreal Engine 5

## Overview

This game dev teaching covers the fundamental lighting tools and techniques in Unreal Engine 5 for creating immersive outdoor environments. It teaches how to use the Environment Light Mixer, configure directional, point, spotlight, and rectangular lights, and apply exponential height fog and volumetric fog for cinematic light rays.

## When to Follow Game Dev Teachings

- When setting up basic outdoor lighting in a new Unreal Engine 5 scene
- When you need to quickly prototype lighting using the Environment Light Mixer
- When working with directional lights to simulate sunlight and soft shadows
- When placing point lights, spotlights, or rectangular area lights for interior or accent lighting
- When adding atmospheric depth with exponential height fog and volumetric fog for cinematic light rays
- When the user asks about light settings such as intensity, attenuation radius, cone angles, or volumetric scattering

## Lessons From Game Dev Teachings

### Lesson 1

#### Examples

##### Example 1: Quick Outdoor Scene Setup

Use the Environment Light Mixer to add sky, sun, and atmospheric fog to an empty level in seconds.

##### Example 2: Cinematic Sunlight with Volumetric Rays

Configure a directional light with high volumetric scattering paired with volumetric fog to create god rays.

##### Example 3: Accent Lighting with a Spotlight

Use a spotlight with custom inner and outer cone angles to highlight a specific object or area.

#### Step 1: Open the Environment Light Mixer

Open the Environment Light Mixer from the Window menu. This tool groups the Sky Light, Directional Light, Sky Atmosphere, and Exponential Height Fog actors for rapid outdoor scene setup.

#### Step 2: Configure the Directional Light (Sun)

Select the Directional Light actor in the Environment Light Mixer and set its Intensity to simulate sunlight brightness. Adjust Light Color to match the desired time-of-day warmth or coolness.

#### Step 3: Adjust Shadow Softness with Source Angle

Set the Source Angle property on the Directional Light. A smaller value produces sharper shadows; a larger value produces softer, more realistic shadows.

#### Step 4: Fine-Tune Indirect Lighting and Volumetrics

Increase Indirect Lighting Intensity to brighten shadowed areas with bounced light. Enable Volumetric Scattering on the Directional Light to allow light rays to pass through fog or dust.

#### Step 5: Set Up a Point Light

Add a Point Light actor to the scene. Adjust Intensity for brightness, Attenuation Radius to control how far the light reaches, and Source Radius to soften shadow edges.

#### Step 6: Set Up a Spotlight

Add a Spotlight actor. Define the Inner Cone Angle for the fully bright core and the Outer Cone Angle for the soft falloff edge. Enable Volumetric on the spotlight if cone-shaped light rays are desired.

#### Step 7: Add a Rectangular Light (Area Light)

Place a Rectangular Light actor to simulate flat light sources such as light panels or windows. This produces very soft shadows but has a higher performance cost.

#### Step 8: Configure Exponential Height Fog

Add an Exponential Height Fog actor to the scene. Adjust fog density and height falloff to create atmospheric depth. This fog gets thicker based on height according to your settings.

#### Step 9: Enable Volumetric Fog for Cinematic Light Rays

In the Exponential Height Fog settings, enable Volumetric Fog. Ensure your lights have Volumetric Scattering enabled so that light interacts with the 3D fog particles to produce visible god rays.

#### Step 10: Toggle Overlays with the G Key

Press the G key to toggle all editor overlays, gizmos, and helper widgets on and off. Use this to preview the scene without visual clutter.

#### Best Practices

- ✅ Start with the Environment Light Mixer for outdoor scenes instead of placing lights manually
- ✅ Use a larger Source Angle for sunlight to simulate a physically large light source like the sun
- ✅ Enable Volumetric Scattering only when needed, as it impacts performance
- ✅ Use Rectangular Lights for soft shadow accents where performance allows
- ✅ Adjust fog density gradually and test in-game to avoid overly thick or thin atmospherics

#### Keep In Mind

- Volumetric Fog and Volumetric Scattering are performance-intensive features; use them judiciously on target hardware
- The G key toggle only affects the editor viewport, not the in-game view
- Exponential Height Fog is primarily height-based and works best for outdoor or large-scale scenes

#### Security & Safety Notes

- No user data, external services, or network access are involved in these editor instructions
- No file system writes outside the project directory are required

#### Common Pitfalls

- **Problem:** Shadows appear too harsh and unrealistic with the Directional Light.
  **Solution:** Increase the Source Angle value on the Directional Light to soften shadow edges.
- **Problem:** Volumetric light rays do not appear in the scene.
  **Solution:** Ensure both Volumetric Fog is enabled on the Exponential Height Fog and Volumetric Scattering is enabled on the contributing light(s).
- **Problem:** Fog looks thick and unrealistic throughout the entire level.
  **Solution:** Adjust Exponential Height Fog density and height falloff, and use Volumetric Fog selectively with appropriate particle scales.

## Glossary / Index

|Term|Definition|
|----|----------|
|Attenuation Radius|The maximum distance a point light's brightness reaches before fading to zero|
|Directional Light|A light that emits parallel rays in a single direction, used to simulate sunlight|
|Environment Light Mixer|A UE5 tool that bundles sky, sun, atmospheric, and fog actors for rapid outdoor lighting setup|
|Exponential Height Fog|A fog actor that thickens based on height to simulate atmospheric depth|
|G Key|Editor shortcut that toggles viewport overlays, gizmos, and helper widgets on and off|
|Inner Cone Angle|The fully bright core angle of a spotlight beam|
|Indirect Lighting Intensity|Controls how much a light contributes to bounced indirect lighting in the scene|
|Light Color|The tint or hue applied to a light source|
|Outer Cone Angle|The angle at which a spotlight beam fully fades out, creating a soft edge|
|Point Light|A light that emits equally in all directions from a single point in space|
|Rectangular Light|An area light that emits from a rectangular surface, producing very soft shadows|
|Source Angle|Controls the physical size of a directional light source, affecting shadow softness|
|Source Radius|Controls the softness of shadows cast by a point light|
|Spotlight|A light that emits within a configurable cone shape|
|Volumetric Fog|3D fog particles that light can interact with to create visible god rays and atmospheric scattering|
|Volumetric Scattering|A light property that allows light to be visible as it passes through volumetric fog or dust|
