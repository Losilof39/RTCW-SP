cmake_minimum_required(VERSION 3.15)

project(extractfuncs)

set(CMAKE_C_STANDARD 90)
#set(CMAKE_C_STANDARD_REQUIRED ON)
#set(CMAKE_C_EXTENSIONS OFF)

set(SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/extractfuncs.c
    ${CMAKE_CURRENT_SOURCE_DIR}/l_log.c
    ${CMAKE_CURRENT_SOURCE_DIR}/l_memory.c
    ${CMAKE_CURRENT_SOURCE_DIR}/l_precomp.c
    ${CMAKE_CURRENT_SOURCE_DIR}/l_script.c
)

add_executable(extractfuncs ${SOURCES})

add_compile_definitions(WIN32 _CONSOLE SCREWUP _CRT_SECURE_NO_WARNINGS)

target_include_directories(extractfuncs PUBLIC 
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/game
    ${CMAKE_CURRENT_SOURCE_DIR}/../botlib
    ${CMAKE_CURRENT_SOURCE_DIR}/../bspc
    ${CMAKE_CURRENT_SOURCE_DIR}/../qcommon
)