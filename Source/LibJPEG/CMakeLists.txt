cmake_minimum_required( VERSION 3.23.0 ) # Current version of CMake when this file was created.

project( LibJPEG LANGUAGES C )

set( HEADER_FILES
	jconfig.h
	jdct.h
	jerror.h
	jinclude.h
	jmemsys.h
	jmorecfg.h
	jpegint.h
	jpeglib.h
	jversion.h
	transupp.h
)

set( SOURCE_FILES
	jaricom.c
	jcapimin.c
	jcapistd.c
	jcarith.c
	jccoefct.c
	jccolor.c
	jcdctmgr.c
	jchuff.c
	jcinit.c
	jcmainct.c
	jcmarker.c
	jcmaster.c
	jcomapi.c
	jcparam.c
	jcprepct.c
	jcsample.c
	jctrans.c
	jdapimin.c
	jdapistd.c
	jdarith.c
	jdatadst.c
	jdatasrc.c
	jdcoefct.c
	jdcolor.c
	jddctmgr.c
	jdhuff.c
	jdinput.c
	jdmainct.c
	jdmarker.c
	jdmaster.c
	jdmerge.c
	jdpostct.c
	jdsample.c
	jdtrans.c
	jerror.c
	jfdctflt.c
	jfdctfst.c
	jfdctint.c
	jidctflt.c
	jidctfst.c
	jidctint.c
#	jmemansi.c
#	jmemdos.c
#	jmemmac.c
	jmemmgr.c
#	jmemname.c
	jmemnobs.c
#	jpegtran.c
	jquant1.c
	jquant2.c
	jutils.c
	transupp.c
)

add_library( LibJPEG STATIC ${HEADER_FILES} ${SOURCE_FILES} )

target_include_directories( LibJPEG
	PUBLIC ./
)