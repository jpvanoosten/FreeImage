cmake_minimum_required( VERSION 3.23.0 ) # Current version of CMake when this file was created.

project( LibJXR LANGUAGES C )

set( COMMON_HEADER_FILES
	common/include/guiddef.h
	common/include/wmsal.h
	common/include/wmspecstring.h
	common/include/wmspecstrings_adt.h
	common/include/wmspecstrings_strict.h
	common/include/wmspecstrings_undef.h
)

source_group( "Header Files/common" FILES ${COMMON_HEADER_FILES} )

set( IMAGE_HEADER_FILES
	image/decode/decode.h
	image/encode/encode.h
	image/sys/ansi.h
	image/sys/common.h
	image/sys/perfTimer.h
	image/sys/strcodec.h
	image/sys/strTransform.h
	image/sys/windowsmediaphoto.h
	image/sys/xplatform_image.h
	image/x86/x86.h
)

source_group( TREE ${CMAKE_CURRENT_SOURCE_DIR} PREFIX "Header Files" FILES ${IMAGE_HEADER_FILES} )

set( JXRGLUELIB_HEADER_FILES
	jxrgluelib/JXRGlue.h
	jxrgluelib/JXRMeta.h
)

source_group( "Header Files/jxrgluelib" FILES ${JXRGLUELIB_HEADER_FILES} )

set( IMAGE_SOURCE_FILES
	image/decode/decode.c
	image/decode/JXRTranscode.c
	image/decode/postprocess.c
	image/decode/segdec.c
	image/decode/strdec.c
	image/decode/strdec_x86.c
	image/decode/strInvTransform.c
	image/decode/strPredQuantDec.c
	image/encode/encode.c
	image/encode/segenc.c
	image/encode/strenc.c
	image/encode/strenc_x86.c
	image/encode/strFwdTransform.c
	image/encode/strPredQuantEnc.c	
	image/sys/adapthuff.c
	image/sys/image.c
	image/sys/perfTimerANSI.c
	image/sys/strcodec.c
	image/sys/strPredQuant.c
	image/sys/strTransform.c	
)

source_group( TREE ${CMAKE_CURRENT_SOURCE_DIR} PREFIX "Source Files" FILES ${IMAGE_SOURCE_FILES} )

set( JXRGLUELIB_SOURCE_FILES
	jxrgluelib/JXRGlue.c
	jxrgluelib/JXRGlueJxr.c
	jxrgluelib/JXRGluePFC.c
	jxrgluelib/JXRMeta.c
)

source_group( "Source Files\\jxrgluelib" FILES ${JXRGLUELIB_SOURCE_FILES} )

add_library( LibJXR STATIC 
	${COMMON_HEADER_FILES}
	${IMAGE_HEADER_FILES} 
	${JXRGLUELIB_HEADER_FILES}
	${IMAGE_SOURCE_FILES}
	${JXRGLUELIB_SOURCE_FILES}
)

target_include_directories( LibJXR
	PRIVATE image/sys jxrgluelib
)
