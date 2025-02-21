# Marble Marcher: Community Edition

### Version 1.4.6

![Logo](https://github.com/WAUthethird/Marble-Marcher-Community-Edition/blob/master/doc/LOGO.PNG)

This is the community edition of Marble Marcher, a procedurally rendered fractal physics marble game in which you must get to the flag in each level as fast as you can. If you complete all 24 original levels, cheats are unlocked for extra fun!

Because version 1.1.0 was the last feature update of Marble Marcher, we (the Marble Marcher Community) opted to create a community edition to keep the community around the game alive and continuously improve the experience.
Currently this is maintained mainly by members of the [Marble Marcher Community on Discord](https://discord.gg/r3XrJxH), in addition to the members of the [subreddit](https://www.reddit.com/r/marblemarcher) and anyone else who has contributed.

Marble Marcher: Community Edition comes with a wealth of new features and improvements, including performance improvements and graphical enhancements.

If you have suggestions, issues, or would like to contribute, feel free to submit issues and pull requests. After all, this is a community project!

Just as the original Marble Marcher, the game is particularly GPU heavy, but nonetheless it is optimized to run about 100% to 200% faster with the same resolution and also has customisable graphics settings.

speedrun.com link: [https://www.speedrun.com/marblemarcher](https://www.speedrun.com/marblemarcher)

itch.io link: [https://michaelmoroz.itch.io/mmce](https://michaelmoroz.itch.io/mmce)

Web port: [https://www.shadertoy.com/view/3lKyDR](https://www.shadertoy.com/view/3lKyDR)

All credit goes to [HackerPoet](https://github.com/HackerPoet) (aka [CodeParade](https://www.youtube.com/channel/UCrv269YwJzuZL3dH5PCgxUw)) for the [original game](https://github.com/HackerPoet/MarbleMarcher).

## Original Summary
*Marble Marcher is a video game demo that uses a fractal physics engine and fully procedural rendering to produce beautiful and unique gameplay unlike anything you've seen before.*

*The goal of the game is to reach the flag as quickly as possible.  But be careful not to*
*fall off the level or get crushed by the fractal!  There are 24 levels to unlock.*

*Download Link: https://codeparade.itch.io/marblemarcher*

*Video Explanation: https://youtu.be/9U0XVdvQwAI*

## Table of Contents
- [Changes](#changes)
- [Proposed changes](#proposed-changes)
- [Graphics settings](#graphics-settings)
- [System Dependencies](#system-dependencies)
  - [macOS](#macos)
  - [Arch Linux](#arch-linux)
- [Building](#building)
  - [macOS](#macos-1)
  - [Arch Linux](#arch-linux-1)
  - [Ubuntu](#ubuntu)
  - [Compiling on Windows](#compiling-on-windows)
  - [Cross-Compile for Windows on macOS](#cross-compile-for-windows-on-macos)
- [Launching](#launching)
  - [macOS](#macos-2)
  - [Other OSes](#windowslinuxanything-else)
- [Special Controls](#special-controls)
- [Troubleshooting/FAQ](#troubleshooting/faq)

## Changes
Compared to the original game, the following features and improvements have been added as of the current version of MMCE:
- New flexible graphics engine which heavily uses compute shaders and allows writing custom shaderpacks, with the ability to edit shaders in real-time
- Redesigned animated interface. A modular interface was built to allow adding new menus in the future.
- Custom level support with a rudimentary level/fractal editor 
- Several new menus (credits, pause, settings, etc.)
- Rudimentary controller support and configurable keyboard controls
- Basic recording/replay functionality
- High resolution screenshots can be taken, up to 10K
- Multiple localisations with Unicode support (translation work still in progress)
- Ingame statistics added (marble speed, ground/air state, ...). Press `o` to toggle.
- Added several new levels
- And dozens of smaller features
![Editor](https://github.com/WAUthethird/Marble-Marcher-Community-Edition/blob/development/doc/EDITOR.PNG)
![Levels](https://github.com/WAUthethird/Marble-Marcher-Community-Edition/blob/development/doc/LEVELS.PNG)
For more changes, please see the [release notes](https://github.com/WAUthethird/Marble-Marcher-Community-Edition/releases).

## Proposed Changes
Though Marble Marcher CE is a largely finished game, there are still several improvements we'd like to implement. Here are our proposed changes:

- ### Fixes
  - Make sure game runs at the same speed everywhere
  - Mouse/camera speed is too fast while skipping cutscenes
- ### User Experience Improvements
  - Pre-built versions for the common operating systems and make them available as GitHub releases (in progress)
  - Make the fractal recoloring from cheats persistent
  - More efficient anti-aliasing modes
  - Toggle to always activate fast cutscenes
  - Better autosplitter integration
- ### New Features
  - Cheat: no drag
  - Custom marble designs
  - Add a script to build for all platforms at once
  - Have MarbleMarcher added to package managers
- ### Currently WIP
  - Recording/replay functionality
  - Debug info screen
  - Cheat: unlock all levels
  - Add creation of macOS `.dmg` for easy distribution.

## Graphics Settings
There are multiple shader configurations in the settings menu.

**main.cfg** -  Default shader configuration, normal rendering with PBR materials and simple ray marched AO. Use this while playing. Also uses TXAA and supports DOF.

**PTGI.cfg** - Path traced global illumination, attempts to simulate light propagation in the fractal scene. It is graphically unstable and requires time for the light samples to converge, so it is not recommended to use while playing. Use it mainly to make screenshots. Uses TXAA, supports DOF.

**original.cfg** - The original Marble Marcher shading, except the AO.

**simple.cfg** - The simplest working shader, use if your computer is a potato.

**neon.cfg** - Makes fractals look like they are glowing clouds.

**noise_test.cfg** - An example of noise and a simplest shader pipeline, mainly useful for development purposes.

The screenshot resolution and rendering resolutions are separate, so you can, for example, play in 720p and take screenshots in 4K. There is also the screenshot samples parameter, the more you use, the better the screenshot will look (if the shader uses temporal denoise).

## System Dependencies
* [Eigen](http://eigen.tuxfamily.org/index.php?title=Main_Page)
* [SFML 2.5.0](https://www.sfml-dev.org)
* [AntTweakBar](http://anttweakbar.sourceforge.net/)
* [GLEW](http://glew.sourceforge.net/)
* [GLM](https://glm.g-truc.net/)
* [CMake](https://cmake.org/)
* [OpenAL](https://www.openal.org/) (in case you get an "OpenAL DLL not found" error while trying to run the software, seems to be Windows-specific)

### MacOS (Currently unsupported, see below)
On macOS these can be conveniently installed using [HomeBrew](https://brew.sh):

`brew install cmake eigen sfml anttweakbar glew glm`

The version of SFML required is 2.5.1 or newer. It has come to my attention that HomeBrew does now have this version (unlike when these instructions where first written) so installing via HomeBrew should work but you can still [download manually](https://www.sfml-dev.org/download/sfml/2.5.1/) if you wish and install using [these instructions](https://www.sfml-dev.org/tutorials/2.5/start-osx.php). You must install the Frameworks option not the dylib option or the build script may fail.
**Note that if HomeBrew installed a version of SFML older than 2.5.1 for some reason or you wish to install manually, you must remove the version of SFML that Brew installed using `brew remove sfml`.**

Alternatively, [vcpkg](https://github.com/Microsoft/vcpkg) can be used though it is unsupported:

`vcpkg install cmake eigen3 sfml anttweakbar`

It may also be possible to use MacPorts which is also unsupported and untested.
### Arch Linux
The packages `eigen`, `sfml`, `glm`, `git`, `cmake` and `make` are on the core, extra and community repositories.
`sudo pacman -S eigen sfml glm git cmake make`
However, `anttweakbar` is on the AUR. Clone and build it yourself, or use and AUR Helper like [yay](https://github.com/Jguer/yay) :
`yay -S anttweakbar`


## Building
### MacOS
#### Build Script

### Please note that the version of OpenGL that ships with MacOS does not work with compute shaders, which MMCE depends upon. Due to this, the MacOS port is considered completely unworking, and there is no current way to run it successfully. The instructions below have been retained, should another option arise in the future.

**Note for the current version: the macOS build is not yet entirely working properly so revert to the previous prerelease as required. SFML is properly included but as of yet, AntTweakBar is not so this executable will not work on machines without it installed.**
Simply run `./macOSBuildExec.sh` ( You can alternatively use macOSBuildBundle which is the old version of the script, which will generate a full .app file instead of a normal unix executable). This will generate the MarbleMarcher executable that can be used like any other application. It can even be used on systems without SFML as SFML is included in the bundle and the binary is relinked to these versions (As stated above it currently does not work on systems without AntTweakBar installed). Currently the script will only do the relinking part properly if you use SFML 2.5.1 specifically however it is planned to allow for any version. If you have another version, the script will still work, the app just won't work on a machine without SFML.
#### Manual
Due to macOS being unable to find GLM_INCLUDE_DIR it is now assumed to be ./glm . In order for this method to work, GLM should now be manually installed into that directory.
* `wget https://github.com/g-truc/glm/releases/download/0.9.9.8/glm-0.9.9.8.zip`
* `unzip ./glm-0.9.9.8.zip`
* `mkdir build && cd build`
* `cmake ..`
* `cmake -DCMAKE_CXX_FLAGS="-I/usr/local/include" ..`
    * If you use `vcpkg`, add the flag `-DCMAKE_TOOLCHAIN_FILE=[path/to/vcpkg]/scripts/buildsystems/vcpkg.cmake`
* `cd ..`
* `cmake --build build`

Note that this just builds a binary and not an Application bundle like you might be used to seeing. To run properly, you must move the binary (which, after building, is `build/MarbleMarcher`). It is not recommended to build the Application bundle manually so no instructions for that are provided however you may peek in `macOSBuildBundle.sh` to see how it is done.

Alternatively, one can use the platform-dependent build system, for example `Make`:

* `make -C build`

### Arch Linux
* `cd ~`
* `git clone https://github.com/WAUthethird/Marble-Marcher-Community-Edition.git`
* `cd Marble-Marcher-Community-Edition`
* `mkdir build && cd build`
* `cmake ..`
* `cd ..`
* `cmake --build build`
* `cp build/MarbleMarcher ./`

Alternatively, you can install the AUR package at [marblemarcher-git](https://aur.archlinux.org/packages/marblemarcher-git/) using your preferred AUR Helper.
* `yay -S marblemarcher-git`

### Ubuntu

The main problem with the installation is the dependency 
_AntTweakBar_, a C++ library with no Ubuntu package.

But the
first and easy step is to ensure that the following development
tools and
libraries are installed: `libsfml-dev`, `libglm-dev`, `libeigen3-dev`,
`libglew-dev`, `cmake`, `libglu1-mesa-dev` and `mesa-common-dev`.  You
can get it done with
```
sudo apt-get install libsfml-dev libglm-dev libeigen3-dev \
     libglew-dev cmake libglu1-mesa-dev mesa-common-dev
```
You may need to install more (or fewer) libraries, depending on what
do you already have on your system.

#### How to Install on Ubuntu 20.04

The first step is
to download and install
[_AntTweakBar_](http://anttweakbar.sourceforge.net/doc/) library.  I
assume you have unpacked it into _Downloads_ folder.  The
installation
is as easy as running `make` in `AntTweakBar/src` folder.  As a result,
_make_ should create `libAntTweakBar.a` and `libAntTweakBar.so` in your
`AntTweakBar/lib` folder.  You may want to move those to a better
location, e.g. into `$HOME/lib`.

This installation can be done with commands
```
cd ~/Downloads/AntTweakBar/src
make
```

The next task is to clone (or download)
[Marble
Marcher](https://github.com/WAUthethird/Marble-Marcher-Community-Edition).
In the following examples we assume you have downloaded
_Marble Marcher_ into _Downloads_-folder as well.
First you create an empty folder _build_ in the _Marble Marcher_
folder, and run _cmake_ from there.  However, and this is important,
for the following compilation step you
also have to specify the location of
`AntTweakBar.h` and
`libAntTweakBar.a` files using the `CPATH` and `LIBRARY_PATH`
environment variables.  You can do all these steps as follows:
```
cd ~/Downloads
git clone https://github.com/WAUthethird/Marble-Marcher-Community-Edition.git
cd Marble-Marcher-Community-Edition
mkdir build
cd build
cmake ..
CPATH="$HOME/Downloads/AntTweakBar/include/" LIBRARY_PATH="$HOME/Downloads/AntTweakBar/lib" cmake --build .
```
This should create an executable file `MarbleMarcher` in the current
`src` folder.

The executable needs `libAntTweakBar.so` run-time library for running.
So when executing it, you have to tell it where the library is by
using `LD_LIBRARY_PATH` environment
variable.  Hence you run the game as
```
LD_LIBRARY_PATH="$HOME/Downloads/AntTweakBar/lib" ./MarbleMarcher
```
Consider moving `libAntTweakBar.so` into a dedicated location for
run-time libraries and configuring your `LD_LIBRARY_PATH`.

Enjoy!

#### Installing on Ubuntu 18.04

Compiling on Ubuntu 18.04 works mostly in the same way as on Ubuntu
20.04.  However, the default _gcc 7.5.0_ is too old for the source
code.  You have to use _gcc 8.4.0_, provided in the package _gcc-8_.  First,
install all the packages required for Ubuntu 20.04.  Thereafter also
install gcc-8:
```
sudo apt-get install libsfml-dev libglm-dev libeigen3-dev \
     libglew-dev cmake libglu1-mesa-dev mesa-common-dev
sudo apt-get install gcc-8
```
Next, as the default gcc is still version 7, we have to tell _make_
and _cmake_ explicitly
that we we want gcc 8 instead.

Open `AntTweakBar/src/Makefile` in a text editor (e.g. _gedit_), 
and set the _make_ variables `CXX` and
`LINK` (see lines 18 and 21) to `gcc-8` and `g++-8`.  
So the relevant lines should
look like
```
CXX      	= gcc-8
CXXFLAGS 	= $(CXXCFG) -Wall -fPIC -fno-strict-aliasing -D_UNIX -D__PLACEMENT_NEW_INLINE
INCPATH  	= -I../include -I/usr/local/include -I/usr/X11R6/include -I/usr/include
LINK     	= g++-8
```
Now run `make` in the _src_-folder as in case of Ubuntu 20.04:
```
cd AntTweakBar/src
make
```

Cloning _Marble Marcher_ on Ubuntu 18.04 works exactly as on Ubuntu 20.04.
But now, when creating cmake environment, we tell _cmake_ that we use
gcc-8 by setting `CC` and `CXX` environment variables.
Otherwise we follow exactly the steps for
Ubuntu 20.04.  So on 18.04 you can do
```
cd ~/Downloads
git clone https://github.com/WAUthethird/Marble-Marcher-Community-Edition.git
cd Marble-Marcher-Community-Edition
mkdir build
cd build             
CC=/usr/bin/gcc-8 CXX=/usr/bin/g++-8 cmake ..
CPATH="$HOME/Downloads/AntTweakBar/include/" LIBRARY_PATH="$HOME/Downloads/AntTweakBar/lib" cmake --build .
```
As above, you should see the executable _MarbleMarcher_
that can be started with
```             
LD_LIBRARY_PATH="$HOME/Downloads/AntTweakBar/lib" ./MarbleMarcher
```


### Compiling on Windows
Windows compilation should work just fine now. It's relatively easy to do without help, but in case you'd like them, [here are some configuring and compiling instructions](build_on_windows.md).

### Cross-Compile for Windows on macOS
This requires you to install wget, mingw-w64, and git (which you probably already have) either with HomeBrew (recommended) or otherwise. Theoretically, you should be able to just run `winMacOSBuild.sh`. There are no manual instructions because due to issues I had to just compile the thing manually which is annoying and has too many steps.

## Launching
### macOS
If the macOS build script was used, simply launch the app as normal, otherwise:
* Make sure that the current working directory contains the `assets` folder
* Run the executable generated by CMake, located in `build` (or a subdirectory)
* If running MarbleMarcher from a tarball and you see a message like

> ./MarbleMarcher: error while loading shared libraries: libsfml-graphics.so.2.5: cannot open shared object file: No such file or directory
You'll just need to run MarbleMarcher with the correct `LD_LIBRARY_PATH`:

```shell
LD_LIBRARY_PATH=`pwd`/usr/lib ./MarbleMarcher
```
### Windows/Linux/Anything Else
Launching should be self-explanatory for these systems, just run the executable file relevant to your system that is generated by the build process.

## Special Controls
* Press `o` to toggle the debug screen.
* Press `F5` to take a screenshot.
* Press `F4` to open AntTweakBar.

## Troubleshooting/FAQ
* Why am I getting compute shader compilation errors?
  - If you are running a release binary fully tested by us to be functional, such as those found in the Releases tab, it is most likely a graphics card or driver issue. Try updating your graphics drivers, and if that doesn't fix the problem, take a look at the card itself. If you are a Radeon user, compute shaders are either unsupported or not fully supported on cards before the HD 7000 series. If this is the case, you will need to upgrade if you would like to play the game. Otherwise, if you compiled it yourself, whether by our official instructions or for a non-supported operating system, please open an issue and post the error logs.
