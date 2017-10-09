cmake_minimum_required (VERSION 3.9)
project (Main CXX)

if(CMAKE_BUILD_TYPE STREQUAL "Debug")
	set (pokedex_VERSION_MAJOR 1)
	set (pokedex_VERSION_MINOR 0)
elseif(CMAKE_BUILD_TYPE STREQUAL "Release")
	set (pokedex_VERSION_MAJOR 2)
	set (pokedex_VERSION_MINOR 1)
endif()

set (poke_SOURCE_DIR "${PROJECT_SOURCE_DIR}/sources/")
set (poke_INCLUDE_DIR "${PROJECT_SOURCE_DIR}/includes/")
set (poke_BINARY_DIR "${PROJECT_BINARY_DIR}/includes/")

configure_file (
  "${poke_INCLUDE_DIR}/version.hpp.in"
  "${poke_BINARY_DIR}/version.hpp"
  )

include_directories("${poke_INCLUDE_DIR}")
include_directories("${poke_BINARY_DIR}")


file(GLOB_RECURSE SOURCES "${poke_SOURCE_DIR}/*.cpp")
add_executable(Main ${SOURCES})