cmake_minimum_required(VERSION 3.12)
project(RegionGrowing)

set(CMAKE_CXX_STANDARD 17)

find_package(OpenCV REQUIRED)
find_package(Threads REQUIRED)

# Add your source files
set(SOURCES
    ./src/main.cpp
    ./src/ImageProcessor.hpp
    ./src/SegmentedRegion.hpp
    ./src/GermsPositioning.hpp
    ./src/ImageUtil.hpp
    ./src/GrowAndMerge.hpp
)

# Create the executable
add_executable(seg ${SOURCES})

# Include OpenCV headers
target_include_directories(seg PRIVATE ${OpenCV_INCLUDE_DIRS})

# Link against OpenCV and Threads
target_link_libraries(seg PRIVATE ${OpenCV_LIBS} Threads::Threads)