<div align="center">
<h1>Better Grass</h1>
</div>

## File location
```
assets/minecraft/optifine/bettergrass.properties
```

## Blocks
Enable or disable Better Grass for individual blocks.

```properties
grass=<true|false>
grass_path=<true|false>
mycelium=<true|false>
podzol=<true|false>
```

## Multi-layer Grass Sides
Allows transparent grass texture to be used as an overlay for the side of grass.

Layer 1 = `grass_side`   
Layer 2 = `grass` (colored by biome)

```properties
grass.multilayer=<true|false>
```

## Textures
Configure which textures should be used. File directory starts from the "textures" folder of the resource pack.

`texture.grass` is colored by biome.

```properties
texture.grass=<texture path>
texture.grass_side=<texture path>
texture.grass_path=<texture path>
texture.grass_path_side=<texture path>
texture.mycelium=<texture path>
texture.podzol=<texture path>
texture.snow=<texture path>
```
