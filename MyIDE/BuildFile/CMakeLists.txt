cmake_minimum_required (VERSION 2)

#If not conbine it, when connnect C and C++ ,it need use extern
SET(CMAKE_C_COMPILER g++) 

project(main)
include_directories(lib)
add_subdirectory(src bin)

SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR})
