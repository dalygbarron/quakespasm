CMAKE_MINIMUM_REQUIRED(VERSION 3.15)
PROJECT(QSS)

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")

ADD_EXECUTABLE(quakespasm
	Quake/bgmusic.c
#	Quake/cd_null.c
	Quake/cd_sdl.c
	Quake/cfgfile.c
	Quake/chase.c
	Quake/cl_demo.c
	Quake/cl_input.c
	Quake/cl_main.c
	Quake/cl_parse.c
	Quake/cl_tent.c
	Quake/cmd.c
	Quake/common.c
	Quake/console.c
	Quake/crc.c
	Quake/cvar.c
	Quake/gl_draw.c
	Quake/gl_fog.c
	Quake/gl_mesh.c
	Quake/gl_model.c
	Quake/gl_refrag.c
	Quake/gl_rlight.c
	Quake/gl_rmain.c
	Quake/gl_rmisc.c
	Quake/gl_screen.c
	Quake/gl_sky.c
	Quake/gl_texmgr.c
	Quake/gl_vidsdl.c
	Quake/gl_warp.c
	Quake/host.c
	Quake/host_cmd.c
	Quake/image.c
	Quake/in_sdl.c
	Quake/keys.c
#	Quake/lodepng.c
	Quake/main_sdl.c
	Quake/mathlib.c
	Quake/menu.c
	Quake/net_bsd.c
	Quake/net_dgrm.c
	Quake/net_loop.c
	Quake/net_main.c
	Quake/net_udp.c
#	Quake/net_win.c
#	Quake/net_wins.c
#	Quake/net_wipx.c
	Quake/pl_linux.c
#	Quake/pl_win.c
	Quake/pr_cmds.c
	Quake/pr_edict.c
	Quake/pr_exec.c
	Quake/r_alias.c
	Quake/r_brush.c
	Quake/r_part.c
	Quake/r_sprite.c
	Quake/r_world.c
	Quake/sbar.c
	Quake/snd_codec.c
	Quake/snd_dma.c
	Quake/snd_mem.c
	Quake/snd_mix.c
	Quake/snd_mp3tag.c
	Quake/snd_sdl.c
	Quake/strlcat.c
	Quake/strlcpy.c
	Quake/sv_main.c
	Quake/sv_move.c
	Quake/sv_phys.c
	Quake/sv_user.c
	Quake/sys_sdl_unix.c
#	Quake/sys_sdl_win.c
	Quake/view.c
	Quake/wad.c
	Quake/world.c
	Quake/zone.c
	Quake/miniz.c
)

find_package(PkgConfig REQUIRED)

FIND_PACKAGE(SDL2 REQUIRED)
TARGET_LINK_LIBRARIES(quakespasm PRIVATE ${SDL2_LIBRARIES})
INCLUDE_DIRECTORIES(quakespasm ${SDL2_INCLUDE_DIRS})

FIND_PACKAGE(OpenGL REQUIRED)
TARGET_LINK_LIBRARIES(quakespasm PRIVATE ${OPENGL_LIBRARIES})
INCLUDE_DIRECTORIES(quakespasm ${OPENGL_INCLUDE_DIRS})

if(APPLE)
  target_link_libraries(quakespasm PRIVATE
    "-framework IOKit"
    "-framework CoreFoundation"  # likely needed as well
    "-framework CoreGraphics"    # if you haven't linked it yet
  )
endif()