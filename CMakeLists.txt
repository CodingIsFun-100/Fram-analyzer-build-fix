cmake_minimum_required(VERSION 3.25)

project(frame_analyzer VERSION 1.0.0 LANGUAGES CXX)

if (NOT DEFINED ENV{GEODE_SDK})
    message(FATAL_ERROR
        "GEODE_SDK is not set. Please define it to point to your Geode SDK."
    )
else()
    message(STATUS "Found Geode: $ENV{GEODE_SDK}")
endif()

# Keep source discovery simple and automatic if you want
file(GLOB_RECURSE FRAME_ANALYZER_SOURCES CONFIGURE_DEPENDS src/*.cpp)

add_library(${PROJECT_NAME} SHARED ${FRAME_ANALYZER_SOURCES})
target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_20)

add_subdirectory("$ENV{GEODE_SDK}" "${CMAKE_CURRENT_BINARY_DIR}/geode")

# Set up dependencies, resources, and link Geode.
setup_geode_mod(${PROJECT_NAME})
