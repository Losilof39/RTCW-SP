cmake_minimum_required(VERSION 3.15)

project(splines)

set(CMAKE_CXX_STANDARD 11)
#set(CMAKE_C_STANDARD_REQUIRED ON)
#set(CMAKE_C_EXTENSIONS OFF)

set(SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/math_angles.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/math_matrix.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/math_quaternion.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/math_vector.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/q_parse.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/q_shared.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/splines.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/util_str.cpp
)

add_library(splines STATIC ${SOURCES})

add_compile_definitions(WIN32 _LIB _CRT_SECURE_NO_WARNINGS)

target_include_directories(splines PUBLIC 
                            ${CMAKE_CURRENT_SOURCE_DIR})