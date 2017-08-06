cmake_minimum_required(VERSION 3.5)
project( protobuf_example )
set( CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11" )
set( CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin" )
set( CMAKE_LIBRARY_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/lib" )
set( CMAKE_ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/lib" )

# Extra settings 
set( CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} /MT"  )
set( CMAKE_CXX_FLAGS_DEBUG   "${CMAKE_CXX_FLAGS_DEBUG}   /MTd" )


find_package( Protobuf REQUIRED )
include_directories( ${PROTOBUF_INCLUDE_DIR} )

file( GLOB PROJECT_SOURCE_FILES *.cpp *.h protobuf_compiled/*.cc protobuf_compiled/*.h)

set( PROJECT_EXTRA_LIBS    "" )


add_executable( protobuf_example ${PROJECT_SOURCE_FILES} )
target_link_libraries( protobuf_example ${PROTOBUF_LIBRARY} )
