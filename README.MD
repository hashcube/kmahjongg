# Steps for compiling and building kmahjongg
# For Linux

Install following packages using apt-get install
* cmake
* extra-cmake-modules
* libkf5declarative-dev
* libkf5newstuff-dev
* libqt5svg5-dev
* libkf5crash-dev
* libkf5kmahjongglib-dev
* libkf5kdegames-dev
* libkf5kdelibs4support-dev

## Path

make sure the path of `mahjong-level-constraint` and `mahjongg-quest` is proper in `openElectron.sh`

## Compiling and building
From the root of this repo run these commands

`mkdir build && cd build`
`cmake .. && make`
`./kmahjongg`

## Before Running
Copy the layouts to ~/.local/share or /usr/share, so the layouts should be in ~/.local/share/kmahjongg/layouts
Copy the backgrounds and the tilesets to ~/.local/share/kmahjongglib/backgrounds and ~/.local/share/kmahjongglib/tilesets etc

## To Play created layouts in Kmahjongg
Open Board Editor to create the layouts and save it wherever the layout files are present e.g ~/.local/share/kmahjongg/layouts.
Also create a corresponding .desktop file referencing this layout
Go to KMahjong Configuration -> Board Layouts and you can see the newly created layout

# For Windows
## Craft tool pre installation guide
- Remove any c/c++ compiler like mingw
- Remove any installed cmake and make
- Disable any antivirus to avoid failures
- Install Python 3

## Installation guide (follow video for right installation)
- Turn on the developer mode in the Windows
- Install Microsoft Visual Studio 2019
- In the visual studio installation add <b>Desktop development with C++</b>
- If the target Windows version is different from the default included sdk in the <b>Desktop development with C++</b>, add another Windows sdk version of the targetting Windows like 10/11 along with the default added one
- After the Visual Studio install add these environment variables:
  - VCINSTALLDIR = C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\
  - VCTOOLSREDISTDIR = C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Redist\MSVC\14.29.30133
- The latest guide to install craft should be included here: https://community.kde.org/Get_Involved/development/Windows
- During the craft install:
  - let the default options be selected(like directory locations to keep path shorter)
  - make sure the Microsoft Visual Studio is selected instead of Mingw

- Start craft cli with: `C:\CraftRoot\craft\craftenv.ps1`
- Install kmahjongg dependencies and build it:
  ```
	craft --buildtype Release kmahjongg
  ```
  - if the build is successful, check the location with `cs kmahjongg`, the path format would be like C:\\_\\[alphanumeric_dir]\kmahjongg[version]
  - check
- Final build location: C:\CraftRoot\bin\ , which contains kmahjongg.exe
- For creating setup:
  ```
  craft nsis
  ```
  ```
  craft --buildtype Release --package kmahjongg
  ```
  - Resolve some missing dependency during the package process:
    ```
    craft -i --buildtype Release libs/runtime
    ```
    ```
    craft -i --buildtype Release dev-utils/snoretoast
    ```
  - Final output setup .exe file is in C:\CraftRoot\temp\
- For running kmhajongg build independently without creating a setup .exe file:
  - Extract the build-template.zip
  - Copy the C:\CraftRoot\bin\ content into build-template\bin\

## Making change to code
- Make change and build:
	- Make changes in C:\\_\\[alphanumeric_dir]\kmahjongg[version]
	- Delete build directory content from C:\\_\\[alphanumeric_dir]\build
	- Then build with: craft --compile kmahjongg
  - After the compilation copy the kmahjongg.exe from C:\\_\\[alphanumeric_dir]\build\bin\ to C:\CraftRoot\bin\

## Failures in compilation
- Some steps or pre install measures were missed for the craft installation, in such case delete the two directories created during craft install, and after completing all the steps reinstall craft
- This one might not be required but try disabling the firewalls completely
