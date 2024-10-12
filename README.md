# Image Segmentation - Region Growing

This project was developed as part of the course *Mif02 - "Computer Graphics and Image Processing"* for the Master's program in Computer Science at the University Claude Bernard Lyon 1, Villeurbanne, France.

The project focuses on image segmentation using the region-growing technique. For more detailed information, please refer to *rapport.pdf*.

### Project Structure

```
.
├── ressources # contains input images 
|   ├── image_couche.png
|   └── image_debout.png
├── src
|   ├── GermsPositioning.hpp
|   ├── GrowAndMerge.hpp
|   ├── ImageProcessor.hpp
|   ├── ImageUtil.hpp
|   ├── main.cpp
|   └── SegmentedRegion.hpp
├── CMakeLists.txt
├── rapport.pdf
└── README.md
```

### Prerequisites

This project relies on OpenCV. Please follow [this link](https://opencv.org/get-started/) to install OpenCV on your system.

### Building and Running the Project

#### Windows

1. **Using Visual Studio 17**:
   * Open PowerShell, navigate to the project directory, and run the following commands:
     * `mkdir build; cd build`
     * `cmake -G "Visual Studio 17 2022" ..`
   * Open the solution `RegionGrowing.sln` in Visual Studio.
   * Build the `seg` project and set it as the startup project.
   * Go to `Debug` -> `seg Debugging Properties` -> `Debugging` -> `Command Arguments`:
     * Add the following command-line arguments:
       * `../ressources/<image to load> <0 or 1 for boundary display> <0 or 1 for colorization mode>`
       * Example: `../ressources/image_debout.png 0 1`
   * Switch to `Release` mode and run the program.

2. **Using CLion**:
   * Open the project in CLion as a `CMake` project.
   * Navigate to `CMake Profiles` -> `Edit CMake Profiles`
     * Add a `Release` profile using Visual Studio as the `Toolchain`.
   * Build the `seg` project and set it as the startup project.
   * Go to `Run` -> `Edit Configurations` -> `Debug` -> `Program Arguments`:
     * Add the following command-line arguments:
       * Example: `../ressources/image_debout.png 0 1`
   * Select the `Release-Visual Studio` CMake profile and run the program.

#### Linux
* Navigate to the project directory and run:
  * `mkdir build; cd build`
  * `cmake -DCMAKE_BUILD_TYPE=Release ..`
  * `make`
* Once the executable is created, you can run it with the following command:
  * Example: `./seg ../ressources/image_debout.png 0 1`

### Command-Line Arguments

The command follows this format: `./seg <path/to/your/image> <display mode> <colorization mode>`
- `<path/to/your/image>`: Path to the image to be processed (mandatory).
- `<display mode>`:
  - 0: Display complete regions.
  - 1: Display only region boundaries.
- `<colorization mode>`:
  - 0: Colorization based on the original image.
  - 1: Random colorization.