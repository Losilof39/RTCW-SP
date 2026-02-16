cmake_minimum_required(VERSION 3.15)

project(wolf)

set(CMAKE_C_STANDARD 90)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_C_EXTENSIONS ON)

set(SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/src/client/cl_cgame.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/client/cl_cin.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/client/cl_console.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/client/cl_input.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/client/cl_keys.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/client/cl_main.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/client/cl_net_chan.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/client/cl_parse.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/client/cl_scrn.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/client/cl_ui.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/qcommon/cm_load.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/qcommon/cm_patch.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/qcommon/cm_polylib.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/qcommon/cm_test.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/qcommon/cm_trace.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/qcommon/cmd.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/qcommon/common.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/qcommon/cvar.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/qcommon/files.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/qcommon/huffman.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/qcommon/md4.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/qcommon/msg.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/qcommon/net_chan.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/game/q_math.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/game/q_shared.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/client/snd_adpcm.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/client/snd_dma.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/client/snd_mem.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/client/snd_mix.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/client/snd_wavelet.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/server/sv_bot.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/server/sv_ccmds.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/server/sv_client.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/server/sv_game.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/server/sv_init.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/server/sv_main.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/server/sv_net_chan.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/server/sv_snapshot.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/server/sv_world.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/qcommon/unzip.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/qcommon/vm.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/qcommon/vm_interpreted.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/qcommon/vm_x86.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/win32/win_input.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/win32/win_main.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/win32/win_net.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/win32/win_shared.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/win32/win_snd.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/win32/win_syscon.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/win32/win_wndproc.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/win32/winquake.rc)

add_subdirectory(src/renderer)
add_subdirectory(src/botlib)
add_subdirectory(src/splines)

add_executable(wolf ${SOURCES})

set_target_properties(wolf PROPERTIES
    WIN32_EXECUTABLE TRUE
)

add_compile_definitions(_WINDOWS WIN32 _CRT_SECURE_NO_WARNINGS)

target_include_directories(wolf PRIVATE 
    ${CMAKE_CURRENT_SOURCE_DIR}/src/botai
    ${CMAKE_CURRENT_SOURCE_DIR}/src/game
    ${CMAKE_CURRENT_SOURCE_DIR}/src/cgame
    ${CMAKE_CURRENT_SOURCE_DIR}/src/client
    ${CMAKE_CURRENT_SOURCE_DIR}/src/qcommon
    ${CMAKE_CURRENT_SOURCE_DIR}/src/ui
    ${CMAKE_CURRENT_SOURCE_DIR}/src/renderer
    ${CMAKE_CURRENT_SOURCE_DIR}/src/server
    ${CMAKE_CURRENT_SOURCE_DIR}/src/win32
)

target_link_libraries(wolf PRIVATE renderer botlib splines winmm ws2_32)