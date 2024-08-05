# ---------------------------------------------------
# CMakeLists.txt
#
# Author: Thomas Choquet <thomas.publique@icloud.com>
# Date: 2024/08/04 18:49:57
# ---------------------------------------------------

cmake_minimum_required(VERSION 3.23)

option(BUILD_SHARED_LIBS "Build using shared libraries" OFF)

project(GLAD)
enable_language(CXX)

add_library(glad ${GLAD_LIBRARY_TYPE})
set_target_properties(glad PROPERTIES CXX_STANDARD 11 CXX_STANDARD_REQUIRED ON)
target_sources(glad PRIVATE "src/glad.c" "include/glad/glad.h" "include/KHR/khrplatform.h")
target_include_directories(glad PRIVATE "src" PUBLIC "include")