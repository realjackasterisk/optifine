<div align="center">
    <h1>Custom Panorama</h1>
</div>

<div align="center">
    <h2>Description</h2>
</div>

Custom Panorama allows you to change the 3D main menu background, as well as the translucent gradient overlay.

<div align="center">
    <h2>File Locations(s)</h2>
</div>

### File: background.properties
Controls the behaviour of the main menu panorama.

```
~/assets/minecraft/optifine/gui/background.properties
```

### Alternative Panorama Folders
Creating additional folders for panorama allow the use of "randomized" menu backgrounds. The random selection is updated in the same way [splash text](https://minecraft.gamepedia.com/Splash) is chosen.

```
~/assets/minecraft/optifine/gui/background1/
~/assets/minecraft/optifine/gui/background2/
~/assets/minecraft/optifine/gui/background3/
...
```

The alternative panorama folders __must__ contain a set of 6 textures similar to those found in `~/assets/minecraft/textures/gui/title/background/`. In addition, you can include a `background.properties` file in each folder to define custom properties depending on which background is picked. Any properties that are omitted here will simply default to the values used in the top-level `background.properties` file.

<div align="center">
    <h2>Properties</h2>
</div>

### Weight (optional)
Sets the weight of the random panorama selection. Higher numbers will make this panorama more likely to show.

```properties
weight=<number>
```

### Blur (optional)
Sets the level of blur for the panorama textures. 3 types of blur are used in the main menu. Be warned, higher levels may decrease the framerate, especially on lower-end machines.

```properties
blur1=<1-64>
blur2=<1-3>
blur3=<1-3>
```

### Overlay Colors (optional)
There are 2 gradient overlays drawn over the background image. If the top and bottom colors are set to 0, the overlay is disabled. The color format is hexidecimal ARGB.    

```properties
overlay1.top=<ARGB HEX>
overlay1.bottom=<ARGB HEX>
overlay2.top=<ARGB HEX>
overlay2.bottom=<ARGB HEX>
```
