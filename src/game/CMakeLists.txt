cmake_minimum_required(VERSION 3.15)

project(qagamex86)

set(CMAKE_C_STANDARD 90)
#set(CMAKE_C_STANDARD_REQUIRED ON)
#set(CMAKE_C_EXTENSIONS OFF)

set(SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/ai_cast.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ai_cast_characters.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ai_cast_debug.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ai_cast_events.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ai_cast_fight.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ai_cast_func_attack.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ai_cast_func_boss1.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ai_cast_funcs.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ai_cast_script.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ai_cast_script_actions.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ai_cast_script_ents.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ai_cast_sight.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ai_cast_think.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../botai/ai_chat.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../botai/ai_cmd.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../botai/ai_dmnet.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../botai/ai_dmq3.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../botai/ai_main.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../botai/ai_team.c
    ${CMAKE_CURRENT_SOURCE_DIR}/bg_animation.c
    ${CMAKE_CURRENT_SOURCE_DIR}/bg_lib.c
    ${CMAKE_CURRENT_SOURCE_DIR}/bg_misc.c
    ${CMAKE_CURRENT_SOURCE_DIR}/bg_pmove.c
    ${CMAKE_CURRENT_SOURCE_DIR}/bg_slidemove.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_active.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_alarm.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_bot.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_client.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_cmds.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_combat.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_items.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_main.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_mem.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_misc.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_missile.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_mover.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_props.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_save.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_script.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_script_actions.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_session.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_spawn.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_svcmds.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_syscalls.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_target.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_team.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_tramcar.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_trigger.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_utils.c
    ${CMAKE_CURRENT_SOURCE_DIR}/g_weapon.c
    ${CMAKE_CURRENT_SOURCE_DIR}/q_math.c
    ${CMAKE_CURRENT_SOURCE_DIR}/q_shared.c)

add_library(qagamex86 SHARED ${SOURCES})

if(MSVC)
    # Force static runtime for this target (Multi-threaded Debug)
    set_target_properties(qagamex86 PROPERTIES
        MSVC_RUNTIME_LIBRARY "MultiThreadedDebug"   # /MTd
    )
endif()

set_target_properties(qagamex86 PROPERTIES
    WINDOWS_EXPORT_ALL_SYMBOLS TRUE
)

add_compile_definitions(WIN32 _WINDOWS BUILDING_REF_GL GAMEDLL _CRT_SECURE_NO_WARNINGS)

target_link_libraries(qagamex86 PRIVATE winmm)

target_include_directories(qagamex86 PUBLIC 
                            ${CMAKE_CURRENT_SOURCE_DIR}
                            ${CMAKE_CURRENT_SOURCE_DIR}/../botai)