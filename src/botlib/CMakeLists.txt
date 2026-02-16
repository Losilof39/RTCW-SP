cmake_minimum_required(VERSION 3.15)

project(botlib)

set(CMAKE_C_STANDARD 90)
#set(CMAKE_C_STANDARD_REQUIRED ON)
#set(CMAKE_C_EXTENSIONS OFF)

set(SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/be_aas_bspq3.c
    ${CMAKE_CURRENT_SOURCE_DIR}/be_aas_cluster.c
    ${CMAKE_CURRENT_SOURCE_DIR}/be_aas_debug.c
    ${CMAKE_CURRENT_SOURCE_DIR}/be_aas_entity.c
    ${CMAKE_CURRENT_SOURCE_DIR}/be_aas_file.c
    ${CMAKE_CURRENT_SOURCE_DIR}/be_aas_main.c
    ${CMAKE_CURRENT_SOURCE_DIR}/be_aas_move.c
    ${CMAKE_CURRENT_SOURCE_DIR}/be_aas_optimize.c
    ${CMAKE_CURRENT_SOURCE_DIR}/be_aas_reach.c
    ${CMAKE_CURRENT_SOURCE_DIR}/be_aas_route.c
    ${CMAKE_CURRENT_SOURCE_DIR}/be_aas_routealt.c
    ${CMAKE_CURRENT_SOURCE_DIR}/be_aas_routetable.c
    ${CMAKE_CURRENT_SOURCE_DIR}/be_aas_sample.c
    ${CMAKE_CURRENT_SOURCE_DIR}/be_ai_char.c
    ${CMAKE_CURRENT_SOURCE_DIR}/be_ai_chat.c
    ${CMAKE_CURRENT_SOURCE_DIR}/be_ai_gen.c
    ${CMAKE_CURRENT_SOURCE_DIR}/be_ai_goal.c
    ${CMAKE_CURRENT_SOURCE_DIR}/be_ai_move.c
    ${CMAKE_CURRENT_SOURCE_DIR}/be_ai_weap.c
    ${CMAKE_CURRENT_SOURCE_DIR}/be_ai_weight.c
    ${CMAKE_CURRENT_SOURCE_DIR}/be_ea.c
    ${CMAKE_CURRENT_SOURCE_DIR}/be_interface.c
    ${CMAKE_CURRENT_SOURCE_DIR}/l_crc.c
    ${CMAKE_CURRENT_SOURCE_DIR}/l_libvar.c
    ${CMAKE_CURRENT_SOURCE_DIR}/l_log.c
    ${CMAKE_CURRENT_SOURCE_DIR}/l_memory.c
    ${CMAKE_CURRENT_SOURCE_DIR}/l_precomp.c
    ${CMAKE_CURRENT_SOURCE_DIR}/l_script.c
    ${CMAKE_CURRENT_SOURCE_DIR}/l_struct.c)

add_library(botlib STATIC ${SOURCES})

add_compile_definitions(WIN32 _LIB BOTLIB _CRT_SECURE_NO_WARNINGS)

target_link_libraries(botlib PRIVATE winmm)

target_include_directories(botlib PUBLIC 
                            ${CMAKE_CURRENT_SOURCE_DIR}
                            ${CMAKE_CURRENT_SOURCE_DIR}/game)