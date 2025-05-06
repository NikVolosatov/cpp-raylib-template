cmake_minimum_required(VERSION 3.24)
project(MY_PROJECT VERSION 1.0 LANGUAGES CXX)

# Dependencies
include(FetchContent)
set(RAYLIB_VERSION 5.5)
FetchContent_Declare(
    raylib
    URL https://github.com/raysan5/raylib/archive/refs/tags/${RAYLIB_VERSION}.tar.gz
    FIND_PACKAGE_ARGS ${RAYLIB_VERSION}
)

set(RAYLIB_BUILD_EXAMPLES OFF CACHE BOOL "Disable raylib examples")
set(RAYLIB_BUILD_TESTS OFF CACHE BOOL "Disable raylib tests")

FetchContent_MakeAvailable(raylib)

file(GLOB SOURCE_FILES "src/*.cpp")

add_executable(${PROJECT_NAME} ${SOURCE_FILES})
target_link_libraries(${PROJECT_NAME} raylib)