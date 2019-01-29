# Simple CMakeLists.txt to build LFS as a static library (assuming Lua is a static library as well)
cmake_minimum_required(VERSION 2.4.4)
project (luafilesystem C)

if(MSVC)
    # set(CMAKE_DEBUG_POSTFIX "d")
    add_definitions(-D_CRT_SECURE_NO_DEPRECATE)
    add_definitions(-D_CRT_NONSTDC_NO_DEPRECATE)
    include_directories(${CMAKE_CURRENT_SOURCE_DIR})
endif()

add_library(luafilesystem STATIC
	src/lfs.c
	src/lfs.h
)

target_link_libraries(luafilesystem
	lua
)

target_include_directories(lua
	SYSTEM INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/src
)
