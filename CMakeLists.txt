cmake_minimum_required(VERSION 3.25)
project(frame_analyzer VERSION 1.0.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# Geode is provided by the build action / SDK toolchain.
find_package(Geode REQUIRED CONFIG)

add_geode_mod(reumeow.frame_analyzer
    src/main.cpp
)
