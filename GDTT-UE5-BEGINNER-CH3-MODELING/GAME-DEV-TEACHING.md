# Unreal Engine 5 Beginner Tutorial Series: Chapter 3 - Modeling Basics

## Overview

This chapter teaches the basics of modeling in Unreal Engine 5, including enabling the Modeling Tools plugin, using the Modeling tab, understanding wireframes and mesh components, and creating a hexagonal spaceship hangar shape using the Extrude Path tool.

## When to Follow Game Dev Teachings

- When you need to create 3D assets directly inside Unreal Engine 5 without external software
- When you want to block out scenes quickly using primitive shapes and the Cube Grid tool
- When you need to reference real-world objects to guide your 3D modeling
- When you are following the complete UE5 beginner tutorial series to build a Star Wars spaceship hangar

## Lessons From Game Dev Teachings

### Lesson 1: Enabling Modeling Tools and Understanding the Interface

#### Examples

##### Example 1: Enabling the Modeling Tools Plugin

Enable the Modeling Tools Editor Mode plugin in Unreal Engine 5 to unlock the Modeling tab and access in-engine modeling tools.

##### Example 2: Setting Up Reference Images

Use PureRef to overlay reference images on top of your viewport while modeling, ensuring you have a clear visual target before starting any 3D work.

#### Step 1: Enable the Modeling Tools Plugin

Go to Edit > Plugins in Unreal Engine, search for "modeling", and enable the "Modeling Tools Editor Mode" plugin. Click Yes when prompted and restart the engine. Save your scene before restarting.

#### Step 2: Access the Modeling Tab

After restarting Unreal Engine, navigate to your project level and locate the Modeling tab at the top of the interface. Click it to open the modeling toolset. You can also use the shortcut Shift + a number key, though the tab click is more reliable.

#### Step 3: Set Up Reference Images

Download and install PureRef (a free reference management tool). Drag and drop reference images from Google Images or your own photos into PureRef. Position the PureRef window on your screen to overlay reference images while you model.

#### Best Practices

- ✅ Always save your scene before enabling new plugins or restarting the engine
- ✅ Use PureRef or similar reference tools before starting any modeling project
- ✅ Update your project when prompted after enabling new plugins
- ✅ Use reference images from multiple angles and sources for better results

#### Keep In Mind

- The Modeling Tools Editor Mode plugin is currently in beta, which means it may occasionally have bugs or unexpected behavior
- The tutorial creates a Star Wars spaceship hangar with a hexagonal shape design
- The instructors recreated the spaceship more than 10 times during development, so expect iteration

#### Security & Safety Notes

- Only download PureRef from its official website
- When downloading reference images, ensure you have the right to use them for your projects

#### Common Pitfalls

- **Problem:** Cannot find the Modeling tab after enabling the plugin.
  **Solution:** Restart Unreal Engine completely and check for any project update popups that need to be accepted.
- **Problem:** Overwhelmed by the modeling tool interface.
  **Solution:** Focus on one tool at a time. The tutorial covers basics first and returns to advanced tools in later chapters.
- **Problem:** Forgetting to click Accept after making changes in the Modeling tab.
  **Solution:** Always click Accept at the bottom of the modeling panel to confirm your changes; otherwise, none of your work will be saved.

### Lesson 2: Modeling Primitives, Wireframes, and Basic Tools

#### Examples

##### Example 1: Creating a Cube with Custom Dimensions

Use the Create tab in the Modeling tool to spawn a cube, adjust its width, depth, and height values, and enable wireframe view to inspect the mesh structure.

##### Example 2: Building a Blocked-Out Scene with Cube Grid

Use the Cube Grid tool to quickly prototype platform layouts, staircases, and level foundations before importing detailed assets.

##### Example 3: Creating a Hexagonal Spaceship Hangar with Extrude Path

Draw a precise hexagon shape on the grid using the Extrude Path tool, then extrude it to create the base geometry of the spaceship hangar.

#### Step 1: Create and Inspect Primitive Shapes

In the Modeling tab, select the Create category. Choose a primitive shape such as a cube or sphere. Adjust width, depth, and height using the sliders. Enable "Show Wireframe" to inspect the mesh's vertices, edges, and faces. Increase subdivisions to add detail and smoothness to the geometry.

#### Step 2: Use the Stair Generator

In the Modeling tab, select the Stair tool. Choose a stair type: Linear, Floating, Curved, or Spiral. Adjust the number of steps, step width, height, and depth to match your scene requirements. Click Accept to generate the stair geometry.

#### Step 3: Block Out a Scene with Cube Grid

Select the Cube Grid tool in the Modeling tab. Click and drag on the floor to define the area of your grid. Use the E and Q shortcuts to raise or lower blocks. Adjust "Blocks Per Step" to change grid resolution. Use this to quickly prototype platforms, towers, and level layouts. Click Accept to finalize.

#### Step 4: Create the Hexagonal Spaceship Shape with Extrude Path

Select the Extrude Path tool. Set the snapping value to 100 units for precise grid placement. Draw the hexagon shape by placing points on the grid: move up 3 units, right 3 units, down 6 units, left 3 units, up 3 units, and back to the origin. Disable snapping for smooth width selection, enable rounded corners, set corner roundness to maximum, and choose the extrusion height. Click to confirm the shape, then rotate it 90 degrees on the X axis to orient it correctly.

#### Best Practices

- ✅ Always click Accept after completing a modeling operation to confirm changes
- ✅ Use wireframe view to inspect mesh structure when learning or debugging
- ✅ Increase subdivisions for smoother geometry, but avoid excessive subdivisions on performance-critical meshes
- ✅ Use Cube Grid for rapid scene blocking before adding detailed assets
- ✅ Use reference images throughout the modeling process

#### Keep In Mind

- Subdivisions increase the number of vertices, edges, and faces, which makes deformation smoother but impacts performance
- The hexagonal spaceship hangar target size is approximately 180 meters in length and 30-40 meters in height
- Rounded corners can be enabled mid-procedure if your shape looks too sharp
- The "Interactive" mode is currently buggy and may crash the engine; use the default setting

#### Security & Safety Notes

- Only use plugins from trusted sources like Epic Games
- Keep backup copies of your project before experimenting with new modeling tools

#### Common Pitfalls

- **Problem:** Extrude Path width only snaps to grid units and won't allow free adjustment.
  **Solution:** Disable the snapping tool at the top of the interface while using Extrude Path.
- **Problem:** Extrude Path shape has sharp corners when rounded appearance is desired.
  **Solution:** Enable the "Rounded Corners" option on the left side of the Extrude Path panel and set the roundness to maximum.
- **Problem:** Engine crashes when using certain modeling tool settings.
  **Solution:** Avoid setting the Extrude Path mode to "Fixed"; keep it on "Interactive" as the Fixed mode is known to crash the engine.

## Glossary / Index

| Term | Definition |
| ---- | ---------- |
| Cube Grid | A modeling tool in Unreal Engine that spawns a grid on the floor for quickly blocking out scene geometry by raising and lowering blocks |
| Edge | A line segment connecting two vertices on a 3D mesh |
| Extrude Path | A modeling tool that lets you draw a 2D shape on a grid and then extrude it into a 3D mesh |
| Face | A flat surface on a 3D mesh bounded by edges |
| High Poly | A mesh with a large number of polygons, allowing for smooth deformation and fine detail |
| Low Poly | A mesh with a small number of polygons, typically used for performance-optimized assets |
| Modeling Tab | The tab in Unreal Engine's editor that contains the in-engine modeling tools and primitives |
| Modeling Tools Editor Mode | A plugin for Unreal Engine 5 that enables the Modeling tab and its associated toolset |
| PureRef | A free reference image management tool that overlays images on your screen while you work in 3D software |
| Snapping | A feature that constrains object movement, rotation, or scaling to specific intervals or grid points |
| Stair Tool | A Modeling tab tool that generates stair geometry with configurable step count, width, height, and style |
| Subdivisions | Additional geometry layers added to a mesh to increase smoothness and deformation capability |
| Vertex | A point in 3D space where edges meet on a mesh |
| Wireframe | A visual representation of a 3D mesh showing its underlying vertices, edges, and faces |
