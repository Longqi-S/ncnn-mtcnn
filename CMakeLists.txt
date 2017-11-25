cmake_minimum_required(VERSION 2.8)
set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fopenmp")
project( MTCNN )
add_executable( mtcnn MTCNN.cpp )

include_directories( ncnn/build/src )
include_directories( ncnn/src )

MESSAGE(${CMAKE_CURRENT_BINARY_DIR})

find_package( OpenCV REQUIRED )
include_directories( ${OpenCV_INCLUDE_DIRS} )

target_link_libraries( mtcnn ${OpenCV_LIBS}  ${CMAKE_CURRENT_SOURCE_DIR}/ncnn/build/src/libncnn.a)
