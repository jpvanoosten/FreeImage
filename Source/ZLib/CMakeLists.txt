# See: https://github.com/madler/zlib for offical ZLib distribution.
cmake_minimum_required( VERSION 3.23.0 ) # Current version of CMake when this file was created.

set( ZLIB_VERSION_MAJOR 1 )
set( ZLIB_VERSION_MINOR 2 )
set( ZLIB_VERSION_PATCH 11 )
set( ZLIB_VERSION ${ZLIB_VERSION_MAJOR}.${ZLIB_VERSION_MINOR}.${ZLIB_VERSION_PATCH} )

project( ZLib VERSION ${ZLIB_VERSION} LANGUAGES C )

set( HEADER_FILES
	crc32.h
	deflate.h
	gzguts.h
	inffast.h
	inffixed.h
	inflate.h
	inftrees.h
	trees.h
	zconf.h
	zlib.h
	zutil.h
)

set( SOURCE_FILES
	adler32.c
	compress.c
	crc32.c
	deflate.c
	gzclose.c
	gzlib.c
	gzread.c
	gzwrite.c
	infback.c
	inffast.c
	inflate.c
	inftrees.c
	trees.c
	uncompr.c
	zutil.c
)

add_library( ZLib STATIC ${HEADER_FILES} ${SOURCE_FILES} )

target_include_directories( ZLib
	PUBLIC ./
)

