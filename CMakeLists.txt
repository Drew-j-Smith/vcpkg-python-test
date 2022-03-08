cmake_minimum_required(VERSION 3.8)

if(NOT DEFINED CMAKE_TOOLCHAIN_FILE)
set(CMAKE_TOOLCHAIN_FILE "./vcpkg/scripts/buildsystems/vcpkg.cmake"
    CACHE STRING "")
endif()

project(test)

find_package(Python3 COMPONENTS Development REQUIRED)

add_executable(test test.cpp)
target_link_libraries(test PRIVATE Python3::Python)