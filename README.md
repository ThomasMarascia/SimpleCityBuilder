# Simple Build System

## Table of Contents
- [Introduction](#introduction)
- [Setup](#setup)
- [Customizations](#customizations)
- [Settings](#settings)
- [Links](#links)
- [Questions?](#questions)
- [License](#license)


## Introduction
This is a simple build system for Unity 3D. It is extremely customizable.


## Setup
1. Download the Asset from the Unity asset store.
2. Import the package.
3. Add either a TerrainBuildArea or MeshBuildArea object to a scene from the Prefab folder. 
4. If using terrain build area, either create a new terrain or edit the demo terrain. If using mesh build area, set the mesh in the mesh build area's mesh filter to any mesh.
5. Setup the build area's settings.
6. If you want the demo's building sceme, add a BuildingManager object to the scene from the Prefab folder. Make sure to add an EventSystem to the scene.
7. If you want the player to be in free cam mode, simply add the UserCamera script to the main camera (example in the BuildSystem_DemoScene scene). If you want to be in first person, add a FirstPersonDemoPlayer object to the scene from the Prefab folder (example in the BuildSystem_FirstPersonScene scene).
8. To add more buildings that are plaecable on the grids, create buildable object data assets and add them to the Build Manager's item list. Example buildable object data assets can be found in the PlaceableObjects folder.


## Customizations

### Adding Buildings:
    The 5 example building data assets are found in BuildSystem/PlaceableObjects. To add more, either duplicate an existing one or right click the content browser and click create->CityBuilder->Buildable Object. Any mesh can be used and will work but the simpler the mesh, the more accurate the grid will be.

### Materials:
    The grid material, building preview materials, and foundation materials are all found in the BuildSystem/Materials folder. 


## Settings

### Build Manager Settings
1. **Item list - Array of Buildable Object Data:** 
    Adding elements allows for more buildings to be placed on the grid by the player.
2. **Max Ray Distance - Float:** 
    Determines how far away a building can be placed from the camera.
3. **Placement Mask - Layers:**
    Adding layers here lets preview buildings be seen while the mouse is not on a build area.

### Build Area Settings
1. **Cell Size - Float:** 
    Determines how big each cell is on the grid. Size is measured in meters (unity's default unit).
2. **Grid Y Offset - Bool:** 
    Determines how much higher/lower the grid is from laying on top of the mesh. In complex mode, this is helpful when max angle and cell size are high. In flat and freeplace modes, this is simply used to change where the buildings are placed mostly.
3. **Y Offset Affect Buildings - Bool:** 
    Determines if buildings follow the Grid Y offset. When set to false, buildings sit on the mesh itself, when set to true, it snaps to the grid.
4. **Free Place - Bool:** 
    If true, no grid will be made and buildings will not snap location.
5. **Grid Mode - Flat or Complex:** 
    Flat mode is extremely simple and works perfectly for a clash of clans type system or other flat meshes/terrains that don't need the grid to follow terrain normals. Complex mode uses sphere casts to make a grid follow hills and valleys of meshes or terrains.
6. **Show Grid - Bool:** 
    If set to false, the grid still exists for the purposes of snapping and placing buildings but it is not visually shown.
7. **Show Grid Only When PLacing Buildings - Bool:** 
    If set to true while show grid is true, the grid is only shown when a building is being previewed on the mesh by the player.
8. **Max Angle - Float:** 
    Determines how big of an angle grid lines are drawn on. If a cell's lines are not drawn, the cell is set to invalid so buildings cannot be placed on it. Under 0 will not drawn any cells. 90 and above should draw lilnes everywhere no matter what (assuming there isn't a hole there).

### Important Grid Overlay Setting
Cell size, cells x, cells z, parent build area, max angle, y offset, and raycast height properties are all controlled by the build area script.
1. **Debug Mode - Bool:** 
    If set to true, debug rays are drawn in the scene window when a grid is being made. Rainbow lines mean sphere cast is hitting. Black lines means sphere cast is missing.
2. **Terrain Mask - Layers:**
    Advanced users only; Changes what layers the sphere cast can hit when finding the verticies of the complex grid. Good if you want more control on where the grid is made on the mesh. 

### Building Object Settings
All of these settings are changed in individual Buildable object data assets.
1. **Object Name - String:** 
    Can be used for UI building name display.
2. **SizeX and SizeZ - Integer:** 
    The size (in grid cells) of the building. X is width, Z is length.
3. **Mesh - Mesh:** 
    The display mesh of the building.
4. **Can Rotate - Bool:**
    Determines if the building can be rotated by the player trying to place it.
5. **Make Foundation - Bool:**
    If true a foundation will be automatically made when the building is placed on uneven ground.
6. **Foundation Mesh - Mesh:**
    What the foundation looks like. Default is a simple cube mesh.
7. **Foundation Material - Material:**
    What material the mesh uses. Default is a solid dark grey material.
8. **Stackable - Bool:**
    If set to true, when the building is placed, it creates a new buildarea on the building so that buildings can be stacked on top of it.
9. **Max Stackable Angle, Grid Y Offset, Y Offset Buildings, Stackable Grid and Mode:** 
    All the same as the corresponding build area settings
10. **Unique Grid Material - Material:** 
    If not set, inherits the grid material from the build area this building is placed on.  

### First Person Demo Player Settings
If using the first person demo player, you can change the move speed, mouse sens, and jump height of the player. This is meant to be used with a build manager set up so setting that up is good as well.


## Links
[Unity Asset Store Package](https://assetstore.unity.com/packages/slug/319108)


## Questions
If there is a suggestion or bug you'd like to report, you can reach out to me either through email: marasciagames@gmail.com or using the [unity asset store page](https://assetstore.unity.com/packages/slug/319108).


## License
As long as you got it on the unity store, use it freely for personal, educational, or commercial projects.
