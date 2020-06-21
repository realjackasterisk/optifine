
<div align="center">
    <h1>Shaders</h1>
</div>

<div align="center">
    <h2>Description</h2>
</div>

Shaders provide the ability to completely overhaul the visual appearance of Minecraft using GLSL shaders. This is based on the [updated Shaders Mod by karyonix.](https://www.minecraftforum.net/forums/mapping-and-modding-java-edition/minecraft-mods/1286604-shaders-mod-updated-by-karyonix)

<div align="center">
    <h2>In-Game Options</h2>
</div>

```
Video Settings... -> Shaders...
```

## Rendering Pipeline
OptiFine shaders make use of a deferred rendering pipeline. The `gbuffer` shaders come first in the pipeline. These render data to textures that will be sent to the `composite` shaders. Optionally, deferred shaders can be added between terrain and water rendering. `composite` shaders then render to textures that will be sent to the `final` shader. The `final` shader renders directly to the screen.
