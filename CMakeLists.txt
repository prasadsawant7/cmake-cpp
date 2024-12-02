# CMake Version (check using => cmake --version)
cmake_minimum_required(VERSION 3.28)

# Project Name
# This sets a variable named as PROJECT_NAME and use it within ${}
project(myproject)

# Recommendation: Set All 3 of the variable when setting a standard
# Sets the standard for c++
set(CMAKE_CXX_STANDARD           20)
# If it doesn't support the requested standard then it will decays back to supported standard by the compiler.
set(CMAKE_CXX_STANDARD_REQUIRED YES)
# Disables compiler-specific extensions for c++.
set(CMAKE_CXX_EXTENSIONS        OFF)

# Find the package
find_package(fmt)

# CMake produces two kinds of outputs
# 1. add_executable()
# 2. add_library()

# What to build and add an executable
# Give source files to build program
add_executable(${PROJECT_NAME} main.cpp)

set(COMMENT [[
Default static
add_library(mylib lib.cpp)

Explicitly static
add_library(mylib STATIC lib.cpp)

This creates a new file libmylib.a
.a extension stands for "archive", it represents an archive of object files (.o files) bundled together into a single file.
.a means it's a static library, which means it's going to be compile directly into whatever code links to it.

If it were a dynamic library it would've linked at runtime.

Shared library or Dynamic library
add_library(mylib SHARED lib.cpp)

This creates a new file libmylib.so
.so extension stands for "shared object" and it is used for shared libraries in Unix-like OS.
So, it creates the dynamic or a shared library.
]])
# add_library(mylib SHARED lib.cpp)

# The created library must be linked to the project
# Add package to the target
target_link_libraries(${PROJECT_NAME} mylib fmt::fmt)

# If the lib.cpp was in lib subdirectroy
add_subdirectory(lib)


