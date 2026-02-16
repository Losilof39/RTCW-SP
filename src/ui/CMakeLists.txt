cmake_minimum_required(VERSION 3.15)

project(uix86)

set(CMAKE_C_STANDARD 90)
#set(CMAKE_C_STANDARD_REQUIRED ON)
#set(CMAKE_C_EXTENSIONS OFF)

set(SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/../game/bg_lib.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../game/bg_misc.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../game/q_math.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../game/q_shared.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ui_atoms.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ui_gameinfo.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ui_main.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ui_players.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ui_shared.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ui_syscalls.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ui_util.c)

add_library(uix86 SHARED ${SOURCES})

if(MSVC)
    # Force static runtime for this target (Multi-threaded Debug)
    set_target_properties(uix86 PROPERTIES
        MSVC_RUNTIME_LIBRARY "MultiThreadedDebug"   # /MTd
    )
endif()

target_include_directories(uix86 PUBLIC 
                            ${CMAKE_CURRENT_SOURCE_DIR}
                            ${CMAKE_CURRENT_SOURCE_DIR}/../game
                            ${CMAKE_CURRENT_SOURCE_DIR}/../../main
                            ${CMAKE_CURRENT_SOURCE_DIR}/../cgame)