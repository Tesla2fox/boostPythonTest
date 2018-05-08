cmake_minimum_required( VERSION 2.8 )
 
project( BoostPythonHelloWorld )
 
# Find necessary packages
find_package( PythonLibs 3 REQUIRED )
include_directories( ${PYTHON_INCLUDE_DIRS} )
 
#find_package( Boost COMPONENTS python REQUIRED )
#include_directories( ${Boost_INCLUDE_DIR} )
#include_directories( "usr/include/" )


#MESSAGE(${Boost_INCLUDE_DIR})
# Build our library
add_library( greet SHARED greet.cpp )
#message(${Boost_Root})

# Define the wrapper library that wraps our library
add_library( greet_ext SHARED greet_ext.cpp )
target_link_libraries( greet_ext boost_python-py35 greet )
# don't prepend wrapper library name with lib
set_target_properties( greet_ext PROPERTIES PREFIX "" )
