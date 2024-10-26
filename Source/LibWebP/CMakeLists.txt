cmake_minimum_required(VERSION 3.20)

# Set the C++ standard to C++17
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(PROJECT_NAME "WebP")

file(GLOB_RECURSE INC
	"./*.h"
)

file(GLOB_RECURSE SRC
	"./*.h"
	"./*.cpp"
	"./*.c"
)

project(${PROJECT_NAME})

add_library(${PROJECT_NAME} STATIC ${SRC} ${INC})
