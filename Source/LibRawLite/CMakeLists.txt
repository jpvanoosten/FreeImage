cmake_minimum_required( VERSION 3.23.0 ) # Current version of CMake when this file was created.

project( LibRawLite LANGUAGES CXX )

set( HEADER_FILES
	internal/defines.h
	internal/libraw_internal_funcs.h
	internal/var_defines.h
	libraw/libraw.h
	libraw/libraw_alloc.h
	libraw/libraw_const.h
	libraw/libraw_datastream.h
	libraw/libraw_internal.h
	libraw/libraw_types.h
	libraw/libraw_version.h	
)

source_group( TREE ${CMAKE_CURRENT_SOURCE_DIR} PREFIX "Header Files" FILES ${HEADER_FILES} )

set( SOURCE_FILES
	internal/dcraw_common.cpp
	internal/dcraw_fileio.cpp
	internal/demosaic_packs.cpp
	src/libraw_c_api.cpp
	src/libraw_cxx.cpp
	src/libraw_datastream.cpp
)

source_group( TREE ${CMAKE_CURRENT_SOURCE_DIR} PREFIX "Source Files" FILES ${SOURCE_FILES} )

add_library( LibRaw STATIC ${HEADER_FILES} ${SOURCE_FILES} )

target_include_directories( LibRaw
	PUBLIC ./
)

target_compile_definitions( LibRaw 
	PUBLIC LIBRAW_NODLL
)
