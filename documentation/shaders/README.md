
<div align="center">
<h1>Shader Packs</h1>
</div>

## Description
Shader packs make use of GLSL

## In-game Settings
`Video Settings... > `

## Rendering Pipeline
OptiFine shaders make use of a deferred rendering pipeline. The `gbuffer` shaders come first in the pipeline. These render data to textures that will be sent to the `composite` shaders. Optionally, deferred shaders can be added between terrain and water rendering. `composite` shaders then render to textures that will be sent to the `final` shader. The `final` shader renders directly to the screen.