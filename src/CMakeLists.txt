cmake_minimum_required(VERSION 3.15)

project(wolf)

set(CMAKE_CXX_STANDARD 11)
#set(CMAKE_C_STANDARD_REQUIRED ON)
#set(CMAKE_C_EXTENSIONS OFF)

set(SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/client/cl_cgame.c
    ${CMAKE_CURRENT_SOURCE_DIR}/client/cl_cin.c
    ${CMAKE_CURRENT_SOURCE_DIR}/client/cl_console.c
    ${CMAKE_CURRENT_SOURCE_DIR}/client/cl_input.c
    ${CMAKE_CURRENT_SOURCE_DIR}/client/cl_keys.c
    ${CMAKE_CURRENT_SOURCE_DIR}/client/cl_main.c
    ${CMAKE_CURRENT_SOURCE_DIR}/client/cl_net_chan.c
    ${CMAKE_CURRENT_SOURCE_DIR}/client/cl_parse.c
    ${CMAKE_CURRENT_SOURCE_DIR}/client/cl_scrn.c
    ${CMAKE_CURRENT_SOURCE_DIR}/client/cl_ui.c
    ${CMAKE_CURRENT_SOURCE_DIR}/qcommon/cm_load.c
    ${CMAKE_CURRENT_SOURCE_DIR}/qcommon/cm_patch.c
    ${CMAKE_CURRENT_SOURCE_DIR}/qcommon/cm_polylib.c
    ${CMAKE_CURRENT_SOURCE_DIR}/qcommon/cm_test.c
    ${CMAKE_CURRENT_SOURCE_DIR}/qcommon/cm_trace.c
    ${CMAKE_CURRENT_SOURCE_DIR}/qcommon/cmd.c
    ${CMAKE_CURRENT_SOURCE_DIR}/qcommon/common.c
    ${CMAKE_CURRENT_SOURCE_DIR}/qcommon/cvar.c
    ${CMAKE_CURRENT_SOURCE_DIR}/qcommon/files.c
    ${CMAKE_CURRENT_SOURCE_DIR}/qcommon/huffman.c
    ${CMAKE_CURRENT_SOURCE_DIR}/qcommon/md4.c
    ${CMAKE_CURRENT_SOURCE_DIR}/qcommon/msg.c
    ${CMAKE_CURRENT_SOURCE_DIR}/qcommon/net_chan.c
    ${CMAKE_CURRENT_SOURCE_DIR}/game/q_math.c
    ${CMAKE_CURRENT_SOURCE_DIR}/game/q_shared.c
    ${CMAKE_CURRENT_SOURCE_DIR}/client/snd_adpcm.c
    ${CMAKE_CURRENT_SOURCE_DIR}/client/snd_dma.c
    ${CMAKE_CURRENT_SOURCE_DIR}/client/snd_mem.c
    ${CMAKE_CURRENT_SOURCE_DIR}/client/snd_mix.c
    ${CMAKE_CURRENT_SOURCE_DIR}/client/snd_wavelet.c
    ${CMAKE_CURRENT_SOURCE_DIR}/server/sv_bot.c
    ${CMAKE_CURRENT_SOURCE_DIR}/server/sv_ccmds.c
    ${CMAKE_CURRENT_SOURCE_DIR}/server/sv_client.c
    ${CMAKE_CURRENT_SOURCE_DIR}/server/sv_game.c
    ${CMAKE_CURRENT_SOURCE_DIR}/server/sv_init.c
    ${CMAKE_CURRENT_SOURCE_DIR}/server/sv_main.c
    ${CMAKE_CURRENT_SOURCE_DIR}/server/sv_net_chan.c
    ${CMAKE_CURRENT_SOURCE_DIR}/server/sv_snapshot.c
    ${CMAKE_CURRENT_SOURCE_DIR}/server/sv_world.c
    ${CMAKE_CURRENT_SOURCE_DIR}/qcommon/unzip.c
    ${CMAKE_CURRENT_SOURCE_DIR}/qcommon/vm.c
    ${CMAKE_CURRENT_SOURCE_DIR}/qcommon/vm_interpreted.c
    ${CMAKE_CURRENT_SOURCE_DIR}/qcommon/vm_x86.c
    ${CMAKE_CURRENT_SOURCE_DIR}/win32/win_input.c
    ${CMAKE_CURRENT_SOURCE_DIR}/win32/win_main.c
    ${CMAKE_CURRENT_SOURCE_DIR}/win32/win_net.c
    ${CMAKE_CURRENT_SOURCE_DIR}/win32/win_shared.c
    ${CMAKE_CURRENT_SOURCE_DIR}/win32/win_snd.c
    ${CMAKE_CURRENT_SOURCE_DIR}/win32/win_syscon.c
    ${CMAKE_CURRENT_SOURCE_DIR}/win32/win_wndproc.c
    ${CMAKE_CURRENT_SOURCE_DIR}/win32/winquake.rc)

add_subdirectory(renderer)
add_subdirectory(cgame)
add_subdirectory(game)
add_subdirectory(ui)
add_subdirectory(botlib)
add_subdirectory(splines)

add_executable(wolf ${SOURCES})

add_compile_definitions(_WINDOWS WIN32 _CRT_SECURE_NO_WARNINGS)

target_include_directories(wolf PRIVATE 
    ${CMAKE_CURRENT_SOURCE_DIR}/botai
    ${CMAKE_CURRENT_SOURCE_DIR}/game
    ${CMAKE_CURRENT_SOURCE_DIR}/cgame
    ${CMAKE_CURRENT_SOURCE_DIR}/client
    ${CMAKE_CURRENT_SOURCE_DIR}/qcommon
    ${CMAKE_CURRENT_SOURCE_DIR}/ui
    ${CMAKE_CURRENT_SOURCE_DIR}/renderer
    ${CMAKE_CURRENT_SOURCE_DIR}/server
    ${CMAKE_CURRENT_SOURCE_DIR}/win32
)

target_link_libraries(wolf PRIVATE renderer cgame game ui botlib splines winmm wsock32)