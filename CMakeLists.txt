cmake_minimum_required(VERSION 3.5)

# Define the module name
set(MODULE_NAME "mod_trial_of_finality")

# Define the source files
set(MODULE_SOURCES
    src/mod_trial_of_finality.cpp
)

# Include AzerothCore directories
include_directories(
    ${CMAKE_SOURCE_DIR}/src/server
    ${CMAKE_SOURCE_DIR}/dep/g3dlite/include
    ${CMAKE_SOURCE_DIR}/dep/gsoap
    ${CMAKE_SOURCE_DIR}/dep/recastnavigation/Recast/Include
    ${CMAKE_SOURCE_DIR}/dep/recastnavigation/Detour/Include
    ${CMAKE_SOURCE_DIR}/dep/recastnavigation/DetourTileCache/Include
    ${CMAKE_BINARY_DIR}
)

# Build your module as a shared library
add_library(${MODULE_NAME} MODULE ${MODULE_SOURCES})

# Link against AzerothCore targets
target_link_libraries(${MODULE_NAME} PRIVATE game shared)

# Set output directories for the built module
set_target_properties(${MODULE_NAME} PROPERTIES
    PREFIX ""
    RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin/modules
    LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin/modules
    ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin/modules
)
