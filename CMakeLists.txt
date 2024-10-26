cmake_minimum_required(VERSION 3.20)

# Set the C++ standard to C++17
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(PROJECT_NAME "freeimage")

file(GLOB_RECURSE INC
    "inc/*.h"
)

file(GLOB_RECURSE SRC
    "Source/*.h"
    "Source/*.cpp"
    "Source/*.c"
)

project(${PROJECT_NAME})

add_library(${PROJECT_NAME} STATIC ${SRC} ${INC})

add_subdirectory(Source/ZLib)
add_subdirectory(Source/OpenEXR)

target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_SOURCE_DIR}/Source/)
