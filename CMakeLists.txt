project(tek)

cmake_minimum_required(VERSION 2.6)

set (VERSION x.xx)

# ==================================================
# Shared library for tek_user
# ==================================================

if (WIN32)
	include_directories(C:\vxi11)
	link_directories(C:\vxi11)
endif (WIN32)

add_library(tek_vxi11 SHARED
	library/tek_vxi11.cc library/tek_vxi11.h
)
target_link_libraries(tek_vxi11 vxi11)

set_target_properties(tek_vxi11 PROPERTIES
	VERSION 0.${VERSION}
	SOVERSION 0
)

# ==================================================
# Command line utilities
# ==================================================

add_executable(tek_afg utils/tek_afg/tek_afg.cc)
target_link_libraries(tek_afg vxi11)

add_executable(tek_afg_upload_arb utils/tek_afg_upload_arb/tek_afg_upload_arb.cc)
target_link_libraries(tek_afg_upload_arb tek_vxi11)

add_executable(tek_load_setup utils/tek_load_save_setup/tek_load_setup.cc)
target_link_libraries(tek_load_setup tek_vxi11)

add_executable(tek_save_setup utils/tek_load_save_setup/tek_save_setup.cc)
target_link_libraries(tek_save_setup tek_vxi11)

add_executable(tgetwf utils/tgetwf/tgetwf.cc)
target_link_libraries(tgetwf tek_vxi11)

