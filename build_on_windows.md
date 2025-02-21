This is a short and easy tutorial for building Marble Marcher: Community Edition on Windows. This tutorial (the command line parts) can be followed with Git Bash, though you'll need a developer CMD in administrator mode for at least one process.

1. Make sure you have [CMake x64](https://cmake.org/download/), [OpenAL](https://www.openal.org/), and [Visual Studio 2022](https://visualstudio.microsoft.com/vs/) installed.

2. Download the CE edition to a folder of your choice and unzip it: [https://github.com/WAUthethird/Marble-Marcher-Community-Edition](https://github.com/WAUthethird/Marble-Marcher-Community-Edition) or `git clone https://github.com/WAUthethird/Marble-Marcher-Community-Edition.git`.

3. Create a folder in your `C:` drive root called `Libraries`. Alternatively, feel free to configure the paths in `CMakeLists.txt`, in the MMCE root.

4. Download and unzip Eigen to the `Libraries` folder. I used the .zip version of the 3.4.0 release: [http://eigen.tuxfamily.org/](http://eigen.tuxfamily.org/)
  * Rename the unzipped folder to `eigen3`.

5. Download and unzip SFML to the `Libraries` folder. I used the 2.5.1 Visual C++ 15 (2017) - 64-bit version: [https://www.sfml-dev.org/download.php](https://www.sfml-dev.org/download.php)
  * Inside the resulting unzipped folder should be just a folder called `SFML-2.5.1`. Move this folder outside its parent folder, into `Libraries`. Delete the now empty parent folder. Rename `SFML-2.5.1` to `SFML-2.5.1_64`.

6. Download and unzip AntTweakBar to the `Libraries` folder: [http://anttweakbar.sourceforge.net](http://anttweakbar.sourceforge.net)
  * Inside the resulting unzipped folder should be just a folder called `AntTweakBar`. Move this folder outside its parent folder, into `Libraries`. Delete the now empty parent folder.

7. Download and unzip GLM to the `Libraries` folder. I used the .zip version of the 0.9.9.8 release: [https://github.com/g-truc/glm/releases/tag/0.9.9.8](https://github.com/g-truc/glm/releases/tag/0.9.9.8)
  * Inside the resulting unzipped folder should be just a folder called `glm`. Move this folder outside its parent folder, into `Libraries`. Delete the now empty parent folder.

8. Download and unzip GLEW to the `Libraries` folder. I used the 2.1.0 Windows binaries: [http://glew.sourceforge.net/](http://glew.sourceforge.net/)
  * Inside the resulting unzipped folder should be just a folder called `glew-2.1.0`. Move this folder outside its parent folder, into `Libraries`. Delete the now empty parent folder. Rename `glew-2.1.0` to `GLEW`.

9. Now that you have all libraries in the proper places, open a developer command prompt with administrator privileges and `cd` into the MMCE root. Run `cmake .`

10. Open the resulting .sln file in Visual Studio and build the solution as a x64 release.

You're done!
If this did not work for you, please open an issue in the repository, or comment on the online Reddit post linked above.
