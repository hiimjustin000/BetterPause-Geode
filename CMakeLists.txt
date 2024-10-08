cmake_minimum_required(VERSION 3.21)
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_OSX_ARCHITECTURES "x86_64;arm64")
set(CMAKE_CXX_VISIBILITY_PRESET hidden)

project(BetterPause VERSION 1.0.0)

file(GLOB SOURCES
	src/*.cpp
)

add_library(${PROJECT_NAME} SHARED ${SOURCES} "src/BetterPause.cpp"  "src/Utils.cpp" "src/BarBetterShow.cpp"  "src/BetterPauseManager.h"  "src/SelectQuickSettings.h" "src/ProgressPlataformerBetter.cpp" "src/BetterInfoUtils.cpp" "src/SetVolumenPopup.cpp" "src/MoreOptionsPauseLayer.cpp" "src/CustomSettings.cpp" "src/Hooks.h" "src/SliderPlus.cpp"   "src/CoinsViewerSprites.cpp")

if (NOT DEFINED ENV{GEODE_SDK})
    message(FATAL_ERROR "Unable to find Geode SDK! Please define GEODE_SDK environment variable to point to Geode")
else()
    message(STATUS "Found Geode: $ENV{GEODE_SDK}")
endif()


add_subdirectory($ENV{GEODE_SDK} ${CMAKE_CURRENT_BINARY_DIR}/geode)

setup_geode_mod(${PROJECT_NAME} EXTERNALS geode.node-ids:1.3.0)