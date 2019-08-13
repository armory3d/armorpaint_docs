# Welcome

![](img/title.jpg)

ArmorPaint is a stand-alone software designed for physically-based texture painting. Drag & drop your 3D models and start painting. Receive instant visual feedback in the viewport as you paint.

>The preview version has many rough edges and the experience may be frustrating.

---

# Download

**Windows** and **Linux** is recommended. An unsigned **macOS** build is also provided. ArmorPaint is a portable application with no installation, just unpack and run.

>[Get ArmorPaint](http://armorpaint.org/download.html)

#### Requirements

Painting process in ArmorPaint runs on the GPU and the performance mainly depends on a graphics card. Minimum for 4K painting is an Intel HD4000 graphics card. For 16K painting, GTX 1060/6GB or better is recommended.

>See [Preferences](http://armorpaint.org/manual/#/?id=preferences) to tune performance.

#### Updating

Latest builds can be downloaded through your [Gumroad Library](http://gumroad.com/library). Alternatively, use the original email sent by Gumroad to access the download page.

>In ArmorPaint, press `Help - Check for Updates...` to check if newer build is available.

<br/><br/><br/><br/><br/>





# Get Started

<iframe width="560" height="315" src="https://www.youtube.com/embed/0LrMx2mmWi0?rel=0" frameBorder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

#### Windows

Unpack downloaded archive and run `ArmorPaint.exe`. In some cases, Windows may prompt you with the unrecognized app dialog - press `More Info - Run Anyway`.

#### Linux

Unpack downloaded archive and run `ArmorPaint`. In some cases, you may need to open terminal in the extracted folder and run `./ArmorPaint`.

#### macOS

*Experimental:* Unsigned app is provided. See `instructions.txt` file in the extracted folder.

#### Controls

- `Left mouse button / Pen` to paint.
- `Alt` + `left mouse button` to rotate the camera.
- `Alt` + `middle mouse button` to pan the camera.
- `Alt` + `right mouse button` / `mouse wheel` to zoom in and out.
- Controls can be customized in `Preferences tab - Keymap`.
- Standard or Blender keymap preset can be selected.

<br/><br/><br/><br/><br/>





# Workflow

![](img/d.jpg)

#### Import Meshes

Drag and drop unwrapped `.obj` file into the viewport. This will replace the currently painted mesh. `.fbx` and `.blend` files are supported, but the importer is not 100% reliable yet.

- Enable `Meshes tab - UDIM Import` to split imported mesh per UDIM tile.
- Enable `Meshes tab - Parse Transforms` to load per-object transforms from `.fbx` file.
- Normals can be re-calculated with `Meshes tab - Geometry - Calculate Normals`.
- Up axis can be set with `Meshes tab - Geometry - Rotate X / Rotate Y / Rotate Z`.
<!-- - `.arm` exporter for Blender can be found [here](https://github.com/armory3d/iron/tree/master/tools). -->

>You can download sample assets for testing [here](https://github.com/armory3d/armorpaint_samples/releases).

#### Import Materials

Drag and drop a folder with PBR texture set onto the viewport. ArmorPaint will recognize the file extensions and create a new material from imported textures.

Click on the `Materials tab - Import` button to import materials from ArmorPaint `.arm` files or Blender `.blend` files. *wip*

>You can download starter content [here](https://github.com/armory3d/armorpaint_lib/releases). *wip*

#### Import Textures

Drag and drop `.jpg`, `.png`, `.tga` or `.hdr` images into the node editor. This will import the image and place a new `Image` node onto the canvas.

#### Export Textures

Click on the `Export tab - Export Textures - Export` button.

- `Layers`: Export all visible layers or selected layers only into textures.
- `Format`: `.png` or `.jpg` (`8bit` color), `.exr` (`16bit / 32bit` color).
- `Channels`: Specify which maps to export into textures.
- `Res`: Set texture resolution.
- `Color`: Set `8bit`, `16bit` or `32bit` textures for painting.

`Output` presets:
- `Generic`: Exports individual PBR textures.
- `Unreal 4`: Exports packed *occlusion-roughness-metallic* texture.
- `Unity 5`: Exports packed *metallic-occlusion-smoothness* texture.

#### Export Mesh

Click on the `Export tab - Export Mesh - Export` button to save the currently loaded mesh into an `.obj` file. This is handy if you only have access to the `.arm` project file.

#### Save / Load Project

Click on the `File - Save` menu item (`Ctrl + S`) to save the currently opened project. Mesh, layers and materials will be saved into `.arm` project file.

To open the project file, drag and drop `.arm` file onto the viewport. `.arm` files can be set to open directly with ArmorPaint executable from the OS file explorer.

`.obj` and other asset types can also be associated if you wish to use ArmorPaint as a model / texture viewer.

<br/><br/><br/><br/><br/>





# Materials

![](img/b.jpg)

Materials in ArmorPaint are composed with nodes. When painting, brush applies a material onto the surface. To compose a material, open node editor by clicking `Materials tab - Nodes` (`TAB`).
- Use toolbar at the top to add new nodes.
- Press `space` to search for nodes.
- Drag textures from `Textures tab` into the node editor to create `Image` nodes.

Material preview is displayed instantly in the `Materials tab` as the nodes are assembled.

Right-click onto material preview to expose material operations:
- Set which channels the material should affect.
- Create fill layer from selected material.
- Delete material.

> Drag and drop material into viewport to create fill layer.

>See [Import Materials](http://armorpaint.org/manual/#/?id=import-materials).

>Implemented material nodes: `Attribute`, `Camera data`, `Fresnel`, `Geometry`, `Layer Weight`, `Object Info`, `RGB`, `Tangent`, `Texture Coord`, `UV Map`, `Value`, `Brick Texture`, `Checker Texture`, `Gradient Texture`, `Image Texture`, `Magic Texture`, `Musgrave Texture`, `Noise Texture`, `Voronoi Texture`, `Wave Texture`, `BrightContrast`, `Gamma`, `HueSatVal`, `Invert`, `MixRGB`, `Vector`, `Bump`, `Mapping`, `Vector Curves`, `Color Ramp`, `Combine HSV`, `Combine RGB`, `Combine XYZ`, `Math`, `RGB to BW`, `Separate HSV`, `Separate RGB`, `Separate XYZ`, `Vector Math`.

<br/><br/><br/><br/><br/>





# Tools

![](img/a.jpg)

#### Brush

![](img/tool_draw.png)

Select `Brush`(`B`) tool from toolbar. Configure brush parameters in the header. Use `left mouse button` / `pen` to paint strokes using the selected material.

- `Radius`: Brush size. (Hold `F` key and move the cursor)
- `UV Scale`: Scale the coords for currently painted material.
- `UV Rotate`: Rotate the coords for currently painted material.
- `Opacity`: Overall opacity of the brush stroke. (Hold `Shift+F` key and move the cursor)
- `Hardness`: Fade opacity towards the brush stroke edge.
- `Blending`: Blending mode used for painting.
- `TexCoord`: Coordinates used for texture sampling. Mesh `UV Map`, `Project` from view or `Triplanar` mapping.
- `X-Ray`: Paint through mesh faces.
- `Symmetry`: Mirror brush strokes on the X, Y and/or Z axis.

#### Eraser

![](img/tool_eraser.png)

Select `Eraser`(`E`) tool from toolbar. Use `left mouse button` / `pen` to erase strokes on the currently selected layer.

- `Radius`: Eraser size.
- `Opacity`: Overall opacity of the eraser stroke.
- `Hardness`: Fade opacity towards the eraser stroke edge.
- `Blending`: Blending mode used for erasing.
- `X-Ray`: Erase through mesh faces.
- `Symmetry`: Mirror eraser strokes on the X, Y and/or Z axis.

#### Fill

![](img/tool_fill.png)

Select `Fill`(`G`) tool from toolbar. Press `left mouse button` / `pen` to fill active layer with selected material. Fill tool respects active object mask, material mask and color id mask.

- `UV Scale`: Scale the coords for currently painted material.
- `UV Rotate`: Rotate the coords for currently painted material.
- `Opacity`: Overall opacity of the fill effect.
- `Blending`: Blending mode used for fill effect.
- `TexCoord`: Coordinates used for texture sampling. Mesh `UV Map`, `Project` from view or `Triplanar` mapping.
- `Fill Mode`: Allows to fill individual mesh faces.

#### Decal

![](img/tool_decal.png)

Select `Decal`(`D`) tool from toolbar. Press `left mouse button` / `pen` to apply active material as a decal onto the surface.

- `Radius`: Decal size.
- `UV Scale`: Scale the coords for currently painted material.
- `UV Rotate`: Rotate the coords for currently painted material.
- `Opacity`: Overall opacity of the decal.
- `Blending`: Blending mode used for applying decal.
- `Mask`: Apply shape mask to the decal.
- `X-Ray`: Apply decal through mesh faces.
- `Symmetry`: Mirror decal on the X, Y and/or Z axis.

#### Text

![](img/tool_text.png)

Select `Text`(`T`) tool from toolbar. Press `left mouse button` / `pen` to apply active material as a text onto the surface. Drag and drop a `.ttf` file into the viewport to change the font.

- `Radius`: Text size.
- `UV Scale`: Scale the coords for currently painted material.
- `UV Rotate`: Rotate the coords for currently painted material.
- `Opacity`: Overall opacity of the text.
- `Blending`: Blending mode used for applying text.
- `Font`: Select which font to apply.
- `Text`: Type a text to apply.
- `X-Ray`: Apply text through mesh faces.
- `Symmetry`: Mirror text on the X, Y and/or Z axis.

#### Clone

![](img/tool_clone.png)

Select `Clone`(`L`) tool from toolbar. Hold `ALT` to set clone source location. Use `left mouse button` / `pen` to clone the material from source location to active location.

- `Radius`: Brush size.
- `Opacity`: Overall opacity of the brush stroke.
- `Blending`: Blending mode used for painting.
- `X-Ray`: Paint through mesh faces.

#### Blur

![](img/tool_blur.png)

Select `Blur`(`U`) tool from toolbar. Use `left mouse button` / `pen` to smudge the material applied to the surface.

- `Radius`: Brush size.
- `Opacity`: Overall opacity of the brush stroke.
- `Blending`: Blending mode used for painting.
- `X-Ray`: Paint through mesh faces.

#### Particle *wip*

![](img/tool_particle.png)

Select `Particle`(`P`) tool from toolbar. Use `left mouse button` / `pen` to apply particles onto the surface.

- `Radius`: Particle emitter size.
- `Opacity`: Overall opacity of the emitted particle.
- `Blending`: Blending mode used for applying particles.
- `X-Ray`: Apply particles through mesh faces.

#### Bake

![](img/tool_bake.png)

Select `Bake`(`K`) tool from toolbar. Press `left mouse button` / `pen` in viewport to apply bake into the base color channel of active layer or mask.

- `AO`: Bake ambient occlusion. `Strength`, `Radius` and `Offset` can be configured.
- `Curvature`: Bake mesh curvature. `Strength`, `Radius` and `Offset` can be configured.
<!-- - `Normal (Tang)`: Bake normal map from high-poly mesh. -->
- `Normal (World)`: Bake world-space normals encoded into (0-1) range.
- `Position`: Bake world-space positions encoded into (0-1) range.
- `TexCoord`: Bake mesh uv map.
- `Material ID`: Bake colored material IDs.
- `Object ID`: Bake colored object IDs.

> Use `Curvature` baker to create [dirt masks](https://armorpaint.org/manual/img/curvature.jpg).

#### Color ID

![](img/tool_colorid.png)

Select `Color ID`(`C`) tool from toolbar. Drag and drop color-id texture onto the viewport and assign it into the `Color ID Map` field. Afterwards, click on a model to pick a specific color. All drawing operations will now be restricted to this color. Picked color can be removed with a `Clear` button.

#### Picker

![](img/tool_picker.png)

Select `Picker`(`V`) tool from toolbar. Press `left mouse button` / `pen` to read material values from the surface. Base color, normal, occlusion, roughness and metallic values will be displayed in the header.

- `Select Material`: When enabled, the material you pick from the mesh surface will also get auto-selected in the `Materials tab`.
- `Mask`: When set to `Material`, all drawing operations will be restricted to the surface where picked material is painted.

<br/><br/><br/><br/><br/>





# Painting

![](img/c.jpg)

#### Layers

To create a new layer, press `Layers tab - New`. Brush will paint onto the currently selected layer.
- Layer can be parented to the specific object by setting the `Object` combo property. This allows to utilize multiple UV maps per project - each object having it's individual UV map.
- Reveal the layer properties by clicking the `+` sign to set layer `opacity`.

Right-click on the layer to expose layer operations:
- Convert layer to `fill layer` or `paint layer`.
- Create a `White Mask` or `Blask Mask`.
- `Merge` the layer down.
- `Duplicate` the layer.
- `Move` the layer up or down.
- `Delete` layer.
- Set which channels the layer should affect.

Right-click on the mask to expose mask operations:
- `Apply` mask to parent layer.
- `Delete` mask.

>Operations for the base (first) layer are restricted.

>Drag textures from `Textures tab` into the viewport to create mask for active layer.

#### 2D View

![](img/f.jpg)

Click `Layers tab - 2D View` to show the channels of the selected layer. The 2D View is updated immediately as you paint. In the top bar, you can select which channel to show or display UV map as a wireframe.

- Paint tools are also usable directly inside the 2D view.
- Press `Textures tab - 2D View` to show selected image inside 2D view.

#### Camera

Set camera type and parameters in the status bar.

- `Orbit` - Rotate camera around the mesh.
- `Rotate` - Rotate mesh around the origin.
- `Fly` - Hold `right mouse button` and move camera freely using the `WASD` and `QE` keys.

Press `menu bar - View` to set specific camera viewpoint.

#### Viewport

- Set `Light` and `Environment` intensity.
- Set `Light Size`.
- Display specific channel in the viewport.
- Enable `Show Envmap` to draw environment map in the viewport.
- Drag and drop a `.hdr` file onto the viewport to change the environment map.
- Show `Wireframe` in the viewport.
- Show 3D `Compass` in the viewport.

#### Brush Mask

To use image as a brush mask:
- Press `Brushes tab - Nodes` to open node editor.
- Drag and drop brush mask image into the node editor.
- [Connect](https://armorpaint.org/manual/img/brush_mask.jpg) newly placed `Image Texture` node to the `Brush Output - Opacity` socket.

<br/><br/><br/><br/><br/>





# Workspaces

![](img/e.jpg)

Select workspace from the header bar:
- `Paint`: Texture painting, material composition.
- `Scene`: Scene composition. *wip*

<br/><br/><br/><br/><br/>





# Preferences

![](img/g.jpg)

##### Interface

- `UI Scale`: Scale up the user interface when running on high-resolution display.
- `Layout`: Pin properties window to the left or right side.
- `Theme`: Select `Dark` or `Light` theme. Theme can be tweaked by editing the `theme_light.arm` file placed in the `/data` folder. A proper theme editor will be provided in the future.

##### Usage

- `Undo Steps`: Set the number of undo steps to preserve. Using less undo steps may improve performance when running on GPU with constrained memory.
- `Paint Bleed (Bias)`: Stretch brush strokes on the uv map to prevent seams.
- `3D cursor`: Enable topological warp for paint cursor with depth and angle rejection.

##### Pen Pressure

- `Brush Radius`: When painting with a pen, pressure affects the radius of brush.
- `Brush Opacity`: Pressure affects the opacity of brush.
- `Brush Hardness`: Pressure affects the hardness of brush.

>When using Wacom tablets on Windows, ensure `Use Windows Ink` option is enabled in [Wacom Tablet Properties](https://armorpaint.org/manual/img/wacom.png).

##### Viewport Quality

On faster GPUs:
- Raise `Super Sample` to 2X/4X for improved anti-aliasing.
- Enable `Voxel AO` for cone-traced ambient occlusion and shadows.

On slower GPUs:
- Disable `SSAO` for improved performance.

>To simulate [pixel-art like](https://armorpaint.org/manual/img/pixelart.png) painting, disable `Filter Textures` option and set `Super Sample` to `0.25x`.

<br/><br/><br/><br/><br/>





# Plugins

To enable plugins, edit the `config.arm` file placed in the `/data` folder. A plugin filename can be entered into the `plugins` array. A proper plugin manager will be provided in the future.

Plugins are written in JavaScript or WebAssembly. For a minimal example, see the bundled [plugin_hello.js](https://github.com/armory3d/armorpaint/blob/master/Bundled/plugins/plugin_hello.js) and [plugin_rotate.js](https://github.com/armory3d/armorpaint/blob/master/Bundled/plugins/plugin_rotate.js) files located in the `/data` folder.

```json
{
	...
	"plugins": ["plugin_hello.js"]
}
```
