cmake_minimum_required( 3.23.0 ) # Current version of CMake when this file was created.

option( FREEIMAGE_BUILD_EXAMPLES "Build examples for FreeImage." ON )
option( FREEIMAGE_BUILD_TESTING "Build test project for FreeImage" OFF )
option( BUILD_SHARED_LIBS "Build shared libraries." ON )

# Use solution folders to organize projects.
set_property(GLOBAL PROPERTY USE_FOLDERS ON)

# Enable multithreaded compilation on MSVC
if(MSVC)
	add_compile_options(/MP)
endif(MSVC)

# Add source directory
add_subdirectory(Source)

if(FREEIMAGE_BUILD_EXAMPLES)
	add_subdirectory(Examples)
endif(FREEIMAGE_BUILD_EXAMPLES)


if(FREEIMAGE_BUILD_TESTING)
	add_subdirectory(TestAPI)
endif(FREEIMAGE_BUILD_TESTING)

