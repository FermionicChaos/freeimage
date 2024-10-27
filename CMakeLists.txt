cmake_minimum_required(VERSION 3.20)
cmake_policy(SET CMP0077 NEW)

# Set the C++ standard to C++14
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(PROJECT_NAME "FreeImage")

# ------------------- FreeImage -------------------

include(FetchContent)

# First fetch ZLib.
FetchContent_Declare(
    ZLib
    GIT_REPOSITORY          https://github.com/madler/zlib.git
    GIT_TAG                 v1.2.11
)
FetchContent_MakeAvailable(ZLib)

# LibJPEG
FetchContent_Declare(
    LibJPEG
    GIT_REPOSITORY          https://github.com/winlibs/libjpeg.git
    GIT_TAG                 libjpeg-9c
)
FetchContent_MakeAvailable(LibJPEG)

# LibJXR (NOT ORIGINAL SOURCE (MICROSOFT GARBAGE))
FetchContent_Declare(
    LibJXR
    GIT_REPOSITORY          https://github.com/4creators/jxrlib.git
    GIT_TAG                 master
)
FetchContent_MakeAvailable(LibJXR)

# LibOpenJPEG
FetchContent_Declare(
    LibOpenJPEG
    GIT_REPOSITORY          https://github.com/uclouvain/openjpeg.git
    GIT_TAG                 v2.4.0
)
FetchContent_MakeAvailable(LibOpenJPEG)

# # LibPNG
# FetchContent_Declare(
#     LibPNG
#     GIT_REPOSITORY          https://github.com/pnggroup/libpng.git
#     GIT_TAG                 v1.6.35
# )
# FetchContent_MakeAvailable(LibPNG)

# LibRawLit
FetchContent_Declare(
    LibRaw
    GIT_REPOSITORY          https://github.com/LibRaw/LibRaw.git
    GIT_TAG                 0.19.0
)
FetchContent_MakeAvailable(LibRaw)

# LibTIFF4
FetchContent_Declare(
    LibTIFF4
    GIT_REPOSITORY          https://gitlab.com/libtiff/libtiff.git
    GIT_TAG                 v4.0.9
)
FetchContent_MakeAvailable(LibTIFF4)

# LibWebP
FetchContent_Declare(
    LibWebP
    GIT_REPOSITORY          https://chromium.googlesource.com/webm/libwebp
    GIT_TAG                 v1.0.0
)
FetchContent_MakeAvailable(LibWebP)

# # OpenEXR
# FetchContent_Declare(
#     OpenEXR
#     GIT_REPOSITORY          https://github.com/AcademySoftwareFoundation/openexr.git
#     GIT_TAG                 v2.3.0
# )
# FetchContent_MakeAvailable(OpenEXR)

file(GLOB_RECURSE INC
    "Source/FreeImage/*.h"
    "Source/FreeImageToolkit/*.h"
    "Source/Metadata/*.h"
    "Source/CacheFile.h"
    "Source/FreeImage.h"
    "Source/FreeImageIO.h"
    "Source/MapIntrospector.h"
    "Source/Plugin.h"
    "Source/Quantizers.h"
    "Source/ToneMapping.h"
    "Source/Utilities.h"
)

file(GLOB_RECURSE SRC
    "Source/FreeImage/*.cpp"
    "Source/FreeImage/*.c"
    "Source/FreeImageToolkit/*.cpp"
    "Source/FreeImageToolkit/*.c"
    "Source/Metadata/*.cpp"
    "Source/Metadata/*.c"
)

project(${PROJECT_NAME})

add_library(${PROJECT_NAME} STATIC ${SRC} ${INC})

target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_SOURCE_DIR}/Source/)
target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_SOURCE_DIR}/Source/OpenEXR/)
target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_SOURCE_DIR}/Source/OpenEXR/Half/)
target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_SOURCE_DIR}/Source/OpenEXR/Iex/)
target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_SOURCE_DIR}/Source/OpenEXR/IexMath/)
target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_SOURCE_DIR}/Source/OpenEXR/IlmImf/)
target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_SOURCE_DIR}/Source/OpenEXR/IlmThread/)
target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_SOURCE_DIR}/Source/OpenEXR/Imath/)
# target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_SOURCE_DIR}/Source/LibJXR/jxrgluelib/)
# target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_SOURCE_DIR}/Source/LibJXR/image/sys/)
# target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_SOURCE_DIR}/Source/ZLib/)

# New Includes


target_include_directories(${PROJECT_NAME} PUBLIC ${FETCHCONTENT_BASE_DIR}/libjxr-src/jxrgluelib/)
target_include_directories(${PROJECT_NAME} PUBLIC ${FETCHCONTENT_BASE_DIR}/libjxr-src/image/sys/)
target_include_directories(${PROJECT_NAME} PUBLIC ${FETCHCONTENT_BASE_DIR}/zlib-src/)
