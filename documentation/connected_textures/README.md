
<div align="center">
    <h1>Connected Textures</h1>
    <h3>Alternate Name(s): CTM</h3>
</div>

<div align="center">
    <h2>Description</h2>
</div>

CTM gives you the ability to replace textures of standard blocks using a variety of custom parameters. This allows you to change blocks based on neighbor blocks, biome, world height, and more. OptiFine also supplies a small set of connected textures by default. This includes connected glass (panes and colored variants), bookshelves, sandstone, and red sandstone.

<div align="center">
    <h2>In-Game Options</h2>
</div>

```
Video Settings... -> Quality... -> Connected Textures: OFF|FAST|FANCY
```

| Option | Default | Description |
| :---: | :---: | :--- |
| `OFF` | ✔️ |  |
| `FAST` |  | Basic CTM textures, without inner seams. |
| `FANCY` |  | Full CTM textures, with inner seams. |

<div align="center">
    <h2>Index</h2>
</div>

- [File Locations(s)](#file-locations)
    - File: *.properties
- [General Properties](#general-properties)
    - Match by Tile
    - Match by Block
    - Weight
    - Method
    - Tiles
    - Faces
    - Biomes
    - Heights
    - Inner Seams
- [Exclusive Properties for "overlay" Method](#overlay-specific-properties)
    - Connect by Tile
    - Connect by Block
    - Tint Index
    - Tint Block
    - Render Layer
- [Exclusive Properties for "random" Method]()
    - Tiles
    - Tile Weights
    - Random Loops
    - Symmetry
    - Linked Textures
- [Exclusive Properties for "repeat" Method]()
    - Tiles
    - Width
    - Height
    - Symmetry
- [Exclusive Properties for "ctm_compact" Method]()
    - CTM Index
- [Footnotes](#footnotes)

<div align="center">
    <h2>File Location(s)</h2>
</div>

### File: `*`.properties
For each block you wish to override with CTM, you must specify a .properties file in the following directory:

```
~/assets/minecraft/optifine/ctm/
```

These files can be organized into sub-folders of any depth, as long as everything stays within this top-level CTM folder. Note that all property names are case-sensitive, and all file paths are relative to `~/assets/minecraft` unless stated otherwise.

<div align="center">
    <h2>General Properties</h2>
</div>

The following properties are shared by **all** CTM methods.

Multiple CTM files can refer to the same block/tile, and they will be processed in alphabetical order by filename. All tile-based entries are checked first before ID-based ones. The first match wins.

### Match by Tile (optional?<sup>[[1]](#matchrequired)</sup>)
Applies this CTM to the specified tiles. You can list any number of tiles, separated by a single space.

```properties
matchTiles=<tile name(s)>
```

Tiles are essentially the name of the texture in `textures/block`, minus the file extension. For example, `dirt.png` would be matched like so:
```properties
matchTiles=dirt
```

To match a tile from another Minecraft mod, you will need to know it's internal name. Using [Botania](https://botaniamod.net/) as an example, this would look something like this:
```properties
matchTiles=botania:blazeblock
```

Finally, you can also specify full paths. As stated before, these are still relative the the `~/assets/minecraft` folder.
```properties
matchTiles=textures/myfolder/mycooltexture.png
```

### Match by Block (optional?<sup>[[1]](#matchrequired)</sup>)
Applies this CTM to specified blocks based on their [namespaced ID.](https://minecraft.gamepedia.com/Namespaced_ID) As of Minecraft 1.13, [numeral IDs are no longer supported due to the Flattening.](https://minecraft.gamepedia.com/The_Flattening)

```properties
matchBlocks=<block ID(s) + any valid properties>
```

Additionally, you may also specify blockstates here. To do so, you must use the following pattern. (optional sections in \<angle brackets\>)
```properties
matchBlocks=<namespace:>name<:property1=value1,value2...:property2=value1,value2...>
```

### Weight (optional)
Sets the weight of this CTM file. Default value is 0.
```properties
weight=<number>
```

If multiple CTM files match the same block/tile, the one with the highest weight is used. In the off-chance of a tie, the file names are compared alphabetically.

### CTM Method
Method to use when choosing the blocks replacement textures.
```properties
method=<method>
```

|         Method        | Tile Count | Description                                   |
|:---------------------:|:----------:|-----------------------------------------------|
|         `ctm`         |     47     | Standard 8-way method.                        |
|     `ctm_compact`     |      5     | Compact version of the 8-way method.          |
|      `horizontal`     |      4     | Only connect to blocks on the left and right. |
|       `vertical`      |      4     | Only connect to blocks above and below.       |
| `horizontal+vertical` |      8     | Connect horizontally, *then* vertically.      |
| `vertical+horizontal` |      8     | Connect vertically, *then* horizontally.      |
|         `top`         |      4     | Only connect to the block above.              |
|        `random`       |     1+     | Pick a tile at random.                        |
|        `repeat`       |     4+     | Apply a fixed pattern over large areas.       |
|        `fixed`        |      1     | Use a single, fixed tile.                     |
|       `overlay`       |     17     | Overlay for transitions between blocks.       |
|     `overlay_ctm`     |     47     | Overlay variant of `ctm` method.              |
|    `overlay_random`   |     1+     | Overlay variant of `random` method.           |
|    `overlay_repeat`   |     4+     | Overlay variant of `repeat` method.           |
|    `overlay_fixed`    |      1     | Overlay variant of `fixed` method.            |

Overlay methods can be conbined with other methods if they come before them in the processing order (alphabetically). The only exception to this is `ctm_compact`.

### Tiles 
List of replacement tiles to use.
```properties
tiles=<tiles>
```

Each tile must be a separate image, just like vanilla block and item textures. Tiles can be specified in several formats, and these formats can be used interchangeably.
| Property Value | Result |
| --- | --- |
| `0` | 0.png |
| `8-11` | 8.png, 9.png, 10.png, 11.png |
| `name` | name.png |
| `name.png` | name.png |
| `<skip>` | Skips this tile. Effectively the same as using a completely transparent texture. **Can only be used by overlay methods.** |
| `<default>` | Uses the default texture for the block/tile. **Cannot be used for overlay methods.** |
| `full/path/name.png` | full/path/name.png |

In all cases but the last, the texture file must be in the same directory as the CTM properties file itself.

<div align="center">
    <h2>Overlay-specific Properties</h2>
</div>

The following properties are used exclusively by the `overlay` method.

### Connect by Tile (optional?)<sup>[[2]](#overlayrequired)</sup>
Connects only to blocks which are using the specified tiles. Effectively uses same type of value as `matchTiles`.
```properties
connectTiles=<tile name(s)>
```

### Connect by Block (optional?)<sup>[[2]](#overlayrequired)</sup>
Connects only to the specified blocks. Effectively uses same type of value as `matchBlocks`.
```properties
connectBlocks=<block ID(s) + any valid properties>
```

### Tint Index (optional)
Specifies the tint index for the tile texture. Default is `-1` (disabled)
```properties
tintIndex=<number>
```

### Tint Block (optional)
The block used for the tile texture tinting. Different blocks use different colors for the same tint index.
```properties
tintBlock=<block ID(s)>
```

### Render Layer (optional)
Sets the layer on which the overlay texture should be rendered.
```properties
layer=<render layer>
```

Acceptable values are as followed:
| Render Layer | Description |
| --- | --- |
| `cutout_mipped` | (Default) Transparent textures with mipmaps. |
| `cutout` | Transparent textures without mipmaps. |
| `translucent` | Translucent textures with mipmaps |

<div align="center">
    <h1>Footnotes</h1>
</div>

<a name="matchrequired">[1]</a> While both of these properties are marked as optional, at least ONE of them is required under normal circumstances. However, if the CTM .properties file is named after the tile/block in question, both of the properties can be safely omitted. Use this table as a quick guide:

| File name | Interpretation |
| :---: | :--- |
| `*`.properties | `matchTiles=<name>` |
| block_`*`.properties | `matchBlocks=<name>` |

<a name="overlayrequired">[2]</a> Similar to the note above, both of these properties are marked as optional, but at least ONE of them is required for the overlay to work properly.
