cmake_minimum_required (VERSION 3.5.1)
project(he_test)

set(CMAKE_CXX_STANDARD 14)

### To use gcc/g++ on a Macintosh, you must set the Compilers
### here, not inside the project
##if(APPLE)
#       set(CMAKE_C_COMPILER "/usr/local/bin/gcc-7")
#       set(CMAKE_CXX_COMPILER "/usr/local/bin/g++-7")
##endif()
### TODO: for now, we use CLang for Mac

find_package(Palisade)

set( CMAKE_CXX_FLAGS ${PALISADE_CXX_FLAGS} )
set( CMAKE_EXE_LINKER_FLAGS ${PALISADE_EXE_LINKER_FLAGS} )

include_directories( ${OPENMP_INCLUDES} )
include_directories( ${PALISADE_INCLUDE} )
include_directories( ${PALISADE_INCLUDE}/third-party/include )
include_directories( ${PALISADE_INCLUDE}/core )
include_directories( ${PALISADE_INCLUDE}/pke )
include_directories( ${PALISADE_INCLUDE}/binfhe )
### add directories for other PALISADE modules as needed for your project

link_directories( ${PALISADE_LIBDIR} )
link_directories( ${OPENMP_LIBRARIES} )
link_libraries( ${PALISADE_LIBRARIES} )

### ADD YOUR EXECUTABLE(s) HERE
### add_executable( EXECUTABLE-NAME SOURCES )
###
### EXAMPLE:
### add_executable( test demo-simple-example.cpp )
add_executable(server server.cpp)
add_executable(encrypt encrypt.cpp)
add_executable(query query.cpp)
add_executable(decrypt decrypt.cpp)
add_executable(ptest ptest.cpp)