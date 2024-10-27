cmake_minimum_required(VERSION 3.20)
cmake_policy(SET CMP0077 NEW)

# Set the C++ standard to C++14
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(PROJECT_NAME "LibJPEG")

file(GLOB_RECURSE INC
    "./*.h"
)

file(GLOB_RECURSE SRC
    "./*.cpp"
    "./*.c"
)

project(${PROJECT_NAME})

add_library(${PROJECT_NAME} STATIC ${SRC} ${INC})

target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/jxrgluelib/)
target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/image/sys/)
