cmake_minimum_required(VERSION 3.31)
project(project_maker CXX ASM_NASM)

set(CMAKE_CXX_STANDARD 26)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

if(CCACHE_FOUND)
    set_property(GLOBAL PROPERTY RULE_LAUNCH_COMPILE ccache)
    message("CCACHE FOUND")
endif()

file(
    GLOB_RECURSE SOURCE_file
    CONFIGURE_DEPENDS
    ${CMAKE_CURRENT_SOURCE_DIR}/SRC/*.cpp
)

file(
    GLOB_RECURSE HEADER_file
    CONFIGURE_DEPENDS
    ${CMAKE_CURRENT_SOURCE_DIR}/INC/*.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/Data_Structure/*.hpp
)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/Data_Structure/)
add_subdirectory(Test)
