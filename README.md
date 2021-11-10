# Zytoskelett VR project

## Table of Contents

[[_TOC_]]

## Project Description

Lorem ipsum undsoweiter

[Link][KRN]

## Installation

### Hardware requirements

- VR Headset
    - Recomended: HTC Vive
- VR-ready PC


### Prerequisites
To start this program in the Unreal Engine 4, you have to install the following programs:
- Unreal Engine version 4.22.3 
- Microsoft Visual Studio 2017 Community or Professional, at least version 15.9.0 

You can download the Unreal Engine [here][UE4]. You need a free epic games account before you can download the Unreal Engine. Choose a creator's license, when asked. Older Visual Studio versions can be found [here][MVS]. A free microsoft account is needed to download and continuously use Visual Studio. Please note that versions of Unreal Engine greater than 4.22 and Visual Studio 2017 **do not currently work**. During installation of visual studio, make sure to install the following workloads: __Desktop development with C++__ and __Game development with C++__ (in german: **Desktopentwicklung mit C++**, **Spieleentwicklung mit C++**) 

### How to run Zytoskelett (TODO: remove)
In order to make the program load in Unreal Engine, you have to open the Visual Studio solution file (called __zytoskelett2.sln__). After Visual Studio finished loading, go to **Build -> Clean Solution** (in german: **Erstellen -> Projektmappe bereinigen**) located in the menu bar at the top of the screen. After that, build your project (**Build -> Build Solution** from the menu bar, **Erstellen -> Projektmappe erstellen** in german). Once the process finished, you can open the project file __zytoskelett2.uproject__ in the Unreal Engine.

## Usage

### Importing Data
In order to load a cytoskeleton into the scene, you need an input file located in the subfolder **Content/Data**, relative to the project's main directory. If it doesn't exist, create it yourself. You will need one line for each vertex of your cell. Each line has to contain the following values:

- a **unique line number** for every filament as an integer. Each vertex belonging to the same filament has the same line number
- a **vertex number** as an integer. Unique for every vertex within the same filament
- its **x-position** as a floating point number 
- its **y-position** as a floating point number
- its **z-position** as a floating point number
- the **density** as a floating point number
- the **azimuth** as a floating point number
- the **elevation** as a floating point number
- its **radius** as a floating point number
- its **length** as a floating point number
- a **distance** as a floating point number
- the **length-distance-ratio** as a floating point number
- a **class identifier**, a number between 1 and 5

All these values are seperated by tabulators. The values have to be in **exactly this order**. No values can be left out.

#### Changing the input files' name

To change the name of the file to import, load your project in the Unreal Engine Editor and select the __Zytoskelett Data__ Actor from the scene browser on the right. In the properties window below, choose **Filename** in the Menu **Zytoskelett - Eingabe** and change the name to your data files name including the file extension (e.g. .dat). Also, an actor is created in the subfolder __Content/Data__ for easy reuse.

### Exporting Data
The changed cytoskeleton can be exported into a file of the same format as the input file. It will have an __\_exported__ added to its input file name. The only adjustable value is a filament's class, so no other values will be changed.

### Data examples
The Zytoskelett project comes with an example file, found here: zytoskelett\Content\Data\ex_003_2_UNREAL.dat
Further Datasets can be found [here][KRNDL].

## How to start the application ...
### ... on PC
#### Controls
You have the following choices for controlling the scene:

- W,A,S,D move through the scene
- The arrow keys rotate the scene
- Left clicking while having a filament selected changes its class to the currently selected one
- Action Button 4 starts importing the chosen file an creating a cytoskeleton in the scene
- Action Button 3 starts exporting an existing cytoskeleton into an output file
- Action Button 1 cycles the currently selected class between 1 and 5
- Action Button 2 stops the VR-Pawn movement and enables the mouse cursor. The filament under the mouse cursor will change its class when left clicking

### ... in VR

#### Controls

##### HP Reverb

##### HTC Vive

![vive controller schematic][viveschem]

*TODO: find a better image with less numbers*

#|Left-hand Controller|Right-hand Controller
--|--|--
1|--|--
2|**up**: move forward<br>**down**: move backwards<br>**left**: move left<br>**right**: move right|**up**: cycle filament class<br>**down**: export data<br>**left**: import data<br>**right**: --
3|-- (Steam Overlay)|--  (Steam Overlay)
4 - 6|--|--
7|--|apply filament class
8|--|--

## Customization

### Change inputs

[UE4]: https://www.unrealengine.com/en-US/download/
[MVS]: https://visualstudio.microsoft.com/de/vs/older-downloads/
[KRN]: http://kernet.rwth-aachen.de/index.html
[KRNDL]: http://kernet.rwth-aachen.de/Downloads.html

[viveschem]: documentation/vive-scheme.png "Vive Controller Schematic"
