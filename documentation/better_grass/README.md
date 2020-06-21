<div align="center">
<h1>Better Grass</h1>
</div>

## Description
Better Grass makes grass blocks blend into the surrounding terrain a bit better by using the top texture on the sides of the block. This can help make gradual hills and other terrain appear more smooth and natural.

## In-Game Settings
```
Video Settings... -> Quality... -> Better Grass: FAST|FANCY|OFF
```

| Option | Default | Description |
| :---: | :---: | :--- |
| `FAST` |  | Grass textures are applied to the sides of ALL grass blocks, regardless of surrounding terrain. |
| `FANCY` |  | Grass textures are only applied when the block is positioned immediately and diagonally to another grass block in vertical space. |
| `OFF` | ✔️ | Grass textures are not applied to the sides of grass blocks. |

## File Location(s)

### File: bettergrass.properties
Controls settings for Better Grass in a resource pack.
```
~/assets/minecraft/optifine/bettergrass.properties
```

## Blocks
Enable or disable Better Grass for individual blocks.

```properties
grass=<true/false>
grass_path=<true/false>
mycelium=<true/false>
podzol=<true/false>
```

## Multi-layer Grass Sides
Allows transparent grass texture to be used as an overlay for the side of grass.

Layer 1 = `grass_side`   
Layer 2 = `grass` (colored by biome)

```properties
grass.multilayer=<true/false>
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
