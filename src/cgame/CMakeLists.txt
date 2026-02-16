cmake_minimum_required(VERSION 3.15)

project(cgamex86)

set(CMAKE_CXX_STANDARD 11)
#set(CMAKE_C_STANDARD_REQUIRED ON)
#set(CMAKE_C_EXTENSIONS OFF)

set(SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/../game/bg_animation.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../game/bg_lib.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../game/bg_misc.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../game/bg_pmove.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../game/bg_slidemove.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_consolecmds.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_draw.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_drawtools.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_effects.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_ents.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_event.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_flamethrower.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_info.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_localents.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_main.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_marks.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_newDraw.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_particles.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_players.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_playerstate.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_predict.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_scoreboard.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_servercmds.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_snapshot.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_sound.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_syscalls.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_trails.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_view.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cg_weapons.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../game/q_math.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../game/q_shared.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../ui/ui_shared.c
)

add_library(cgamex86 SHARED ${SOURCES})

add_compile_definitions(WIN32 _WINDOWS CGAMEDLL _CRT_SECURE_NO_WARNINGS)

target_link_libraries(cgamex86 PRIVATE odbc32 odbccp32)

target_include_directories(cgamex86 PUBLIC 
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/game
    ${CMAKE_CURRENT_SOURCE_DIR}/../ui
    ${CMAKE_CURRENT_SOURCE_DIR}/../../main/ui
)