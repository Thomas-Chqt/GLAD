# ---------------------------------------------------
# CMakeLists.txt
#
# Author: Thomas Choquet <thomas.publique@icloud.com>
# Date: 2024/08/04 18:49:57
# ---------------------------------------------------

cmake_minimum_required(VERSION 3.16)

option(BUILD_SHARED_LIBS "Build using shared libraries" OFF)

project(GLAD)
enable_language(C)

if(NOT CMAKE_RUNTIME_OUTPUT_DIRECTORY)
    set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin")
endif()

if(NOT CMAKE_LIBRARY_OUTPUT_DIRECTORY)
    set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/lib")
endif()

if(NOT CMAKE_ARCHIVE_OUTPUT_DIRECTORY)
    set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/lib")
endif()

add_library(glad)
set_target_properties(glad PROPERTIES C_VISIBILITY_PRESET hidden)

target_sources(glad PRIVATE "src/glad.c" "include/glad/glad.h" "include/KHR/khrplatform.h")
target_include_directories(glad PRIVATE "src" PUBLIC "include")

if(BUILD_SHARED_LIBS)
    target_compile_definitions(glad PRIVATE GLAD_GLAPI_EXPORT_BUILD PUBLIC GLAD_GLAPI_EXPORT)
endif()