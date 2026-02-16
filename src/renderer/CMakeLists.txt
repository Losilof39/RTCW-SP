cmake_minimum_required(VERSION 3.15)

project(renderer)

set(CMAKE_C_STANDARD 90)
#set(CMAKE_C_STANDARD_REQUIRED ON)
#set(CMAKE_C_EXTENSIONS OFF)

set(SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_animation.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_backend.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_bsp.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_cmds.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_cmesh.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_curve.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_flares.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_font.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_image.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_init.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_light.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_main.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_marks.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_mesh.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_model.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_noise.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_scene.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_shade.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_shade_calc.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_shader.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_shadows.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_sky.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_surface.c
    ${CMAKE_CURRENT_SOURCE_DIR}/tr_world.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../win32/win_gamma.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../win32/win_glimp.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../win32/win_qgl.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jcapimin.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jccoefct.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jccolor.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jcdctmgr.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jchuff.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jcinit.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jcmainct.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jcmarker.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jcmaster.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jcomapi.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jcparam.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jcphuff.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jcprepct.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jcsample.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jctrans.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jdapimin.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jdapistd.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jdatadst.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jdatasrc.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jdcoefct.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jdcolor.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jddctmgr.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jdhuff.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jdinput.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jdmainct.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jdmarker.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jdmaster.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jdpostct.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jdsample.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jdtrans.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jerror.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jfdctflt.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jidctflt.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jmemmgr.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jmemnobs.c
    ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6/jutils.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ahangles.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ahglobal.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ahglyph.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ahhint.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ahmodule.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ahoptim.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ftcalc.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ftdebug.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ftextend.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ftglyph.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ftgrays.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ftinit.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ftlist.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ftmm.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ftnames.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ftobjs.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ftoutln.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ftraster.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ftrend1.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ftsmooth.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ftstream.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ftsystem.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/sfdriver.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/sfobjs.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ttcmap.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ttdriver.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ttgload.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ttinterp.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ttload.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ttobjs.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ttpload.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ttpost.c
	${CMAKE_CURRENT_SOURCE_DIR}/../ft2/ttsbit.c
)

add_library(renderer STATIC ${SOURCES})

add_compile_definitions(WIN32 _LIB _CRT_SECURE_NO_WARNINGS)

target_include_directories(renderer PUBLIC 
                            ${CMAKE_CURRENT_SOURCE_DIR}
                            ${CMAKE_CURRENT_SOURCE_DIR}/../qcommon
                            ${CMAKE_CURRENT_SOURCE_DIR}/../win32
                            ${CMAKE_CURRENT_SOURCE_DIR}/../jpeg-6
                            ${CMAKE_CURRENT_SOURCE_DIR}/../game
                            ${CMAKE_CURRENT_SOURCE_DIR}/../cgame
                            ${CMAKE_CURRENT_SOURCE_DIR}/../ft2
)