# Zytoskelett VR project

## Table of Contents

[[_TOC_]]

## Project Description

Keratin intermediate filaments are protein threads that are located inside cells of epithelial tissues such as skin and are responsible for the mechanical stability of these tissues.

This project allows you to view these filaments in a 3-Dimensional space, either in VR or on your Desktop and provides you with the tool to classify and color them to your specifications.
it was created in cooperation with Prof. Dr. rer. nat. Reinhard Windoffer from the [Institute of Molecular and Cellular Anatomy of the RWTH Aachen University Hospital][KRN]

## Installation

### Hardware requirements

- VR Headset (Recomended: HTC Vive)
- VR-ready PC


### Software requirements
- **Unreal Engine 4.22.3**
  
  You can download the Unreal Engine [here][UE4]. You need a free epic games account before you can download the Unreal Engine. Choose a creator's license, when asked.
- **Microsoft Visual Studio 2017** Community or Professional, at least version 15.9.0 

    Older Visual Studio versions can be found [here][MVS]. A free microsoft account is needed to download and continuously use Visual Studio. 
    <br>During installation of visual studio, make sure to install the following workloads: __Desktop development with C++__ and __Game development with C++__
    
> Please note that versions of Unreal Engine greater than 4.22 and Visual Studio 2017 **do not currently work**. 

### How to run Zytoskelett

First you have to clone this repository with the following command: 
```bash
git clone --recurse-submodules https://devhub.vr.rwth-aachen.de/VR-Group/zytoskelett.git
```
In order to start the Project, navigate to the root directory and double-click the __zytoskelett2.uproject__ file. If you have multiple Unreal Engines installed, make sure to launch it with 4.22.3.

## Usage

### Importing Data
In order to load a cytoskeleton into the scene, you need an input file located in the subfolder **Content/Data**, relative to the project's root directory. If it doesn't exist, create it yourself. You will need one line for each vertex of your cell. Each line has to contain the following values:

- **n_segment** as an integer for every filament. Each vertex belonging to the same filament has the same line number
- **n_vert** as an integer. Unique for every vertex within the same filament
- **x-position** as a floating point number 
- **y-position** as a floating point number
- **z-position** as a floating point number
- **density** as a floating point number
- **class identifier**, a number between 1 and 5
  - **TODO:**
  - 1 equals color
  - 2 equals color
  - 3 equals color
  - 4 equals color
  - 5 equals color

All these values are seperated by tabulators. The values have to be in **exactly this order**. No values can be left out.

Example:
```
n_segment	n_vert	x	y	z	density	class	flag
1	1	10.2	20.34	3.17	1422.89875	1	NaN
1	2	10.23	20.4	3.23	1422.89875	1	NaN
2	1	10.53	20.72	3.59	1964.99	1	NaN
2	2	10.62	20.81	3.56	1964.99	1	NaN
```

#### Changing the input files' name

To change the name of the file to import, load your project in the Unreal Engine Editor and select the __Zytoskelett Data__ Actor from the scene browser on the right. In the properties window below, choose **Filename** in the Menu **Zytoskelett - Eingabe** and change the name to your data files name including the file extension (e.g. .dat). Also, an actor is created in the subfolder __Content/Data__ for easy reuse.

### Exporting Data
The changed cytoskeleton can be exported into a file of the same format as the input file. It will have an __\_exported__ added to its input file name. The only value that will be changed is the class, so when importing that file the next time your filaments will keep their assigned class.

### Data examples
The Zytoskelett project comes with an example file, found here: zytoskelett\Content\Data\ex_003_2_UNREAL.dat
Further Datasets can be found [here][KRNDL].

## How to control the application ...
### ... on PC
You can select different viewport options by clicking the little arrow on the right side of the __Play__ button.
![dropdownmenu for viewport selection][UEPlay]

#### Controls
You have the following choices for controlling the scene:

![keyboard control scheme][keybschem]

- W,A,S,D move through the scene
- The arrow keys rotate the scene
- Left clicking while having a filament selected changes its class to the currently selected one
- Action Button 4 starts importing the chosen file an creating a cytoskeleton in the scene
- Action Button 3 starts exporting an existing cytoskeleton into an output file
- Action Button 1 cycles the currently selected class between 1 and 5
- Action Button 2 stops the VR-Pawn movement and enables the mouse cursor. The filament under the mouse cursor will change its class when left clicking

### ... in VR

#### Controls

##### HTC Vive

![vive controller schematic][viveschem]

|||
|----|--------------------------|
| 1  | move forward             |
| 2  | move backward            |
| 3  | move left                |
| 4  | move right               |
| 5  | Assign Class to Filament |
| 6  | Import Data     |
| 7  | Cycle Filament Class |
| 8  | --              |
| 9  | Export Data     |
| 10 | Assign Class to Filament |

#### Valve Index

![steam controller schematic][steamschem]

|||
|----|--------------------------|
| 1  | __up:__ move forward <br> __down:__ move backward <br> __left:__ move left <br> __right:__ move right |
| 2  | __up:__ move forward <br> __down:__ move backward <br> __left:__ move left <br> __right:__ move right |
| 3  | Assign Class to Filament |
| 4  | __up:__ Cycle Filament Class <br> __down:__ Export Data <br> __left:__ Import Data <br> __right:__ Export Data |
| 5  | __up:__ Cycle Filament Class <br> __down:__ Export Data <br> __left:__ Import Data <br> __right:__ Export Data |
| 6  | Assign Class to Filament     |

##### HP Reverb



## Customization

### Change inputs

[UE4]: https://www.unrealengine.com/en-US/download/
[MVS]: https://visualstudio.microsoft.com/de/vs/older-downloads/
[KRN]: http://kernet.rwth-aachen.de/index.html
[KRNDL]: http://kernet.rwth-aachen.de/RPE-main.html

[viveschem]: documentation/vive-controls.jpg "Vive Controller Schematic"
[steamschem]: documentation/steam-controls.jpg "Steam Controller Schematic"
[keybschem]: documentation/keyboard-controls.jpg "Keyboard Control Schematic"
[UEPlay]: documentation/unreal-play.png "Viewport Selection"



[//]: # In order to make the program load in Unreal Engine, you have to open the Visual Studio solution file (called __zytoskelett2.sln__). After Visual Studio finished loading, go to **Build -> Clean Solution** (in german: **Erstellen -> Projektmappe bereinigen**) located in the menu bar at the top of the screen. After that, build your project (**Build -> Build Solution** from the menu bar, **Erstellen -> Projektmappe erstellen** in german). Once the process finished, you can open the project file __zytoskelett2.uproject__ in the Unreal Engine.