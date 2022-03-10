cmake_minimum_required(VERSION 3.8)

if(NOT DEFINED CMAKE_TOOLCHAIN_FILE)
set(CMAKE_TOOLCHAIN_FILE "./vcpkg/scripts/buildsystems/vcpkg.cmake"
    CACHE STRING "")
endif()

project(test)

find_package(Python3 COMPONENTS Development REQUIRED)

add_executable(test test.cpp)
target_link_libraries(test PRIVATE Python3::Python)

if(WIN32)
    add_custom_command(TARGET test POST_BUILD 
    COMMAND ${Python3_EXECUTABLE} -m venv $<TARGET_FILE_DIR:test>/..
    COMMAND $<TARGET_FILE_DIR:test>/../Scripts/activate.bat
    COMMAND python -m pip install -r ${CMAKE_SOURCE_DIR}/requirements.txt > pip_install.log)
else()
    add_custom_command(TARGET test POST_BUILD 
    COMMAND ${Python3_EXECUTABLE} -m venv $<TARGET_FILE_DIR:test>/..
    COMMAND $<TARGET_FILE_DIR:test>/../Scripts/activate
    COMMAND python -m pip install -r ${CMAKE_SOURCE_DIR}/requirements.txt > pip_install.log)
endif()