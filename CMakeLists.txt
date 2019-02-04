cmake_minimum_required(VERSION 2.6)
project(generator)

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")

include(GNUInstallDirs)

if(MSVC)
	add_definitions(/W3)
else()
	add_definitions(-std=c++11 -pedantic -Wall -Wextra)
endif()

include_directories(${CMAKE_SOURCE_DIR}/include)
add_definitions(-DGENERATOR_USE_GLM -DGLM_ENABLE_EXPERIMENTAL)
include_directories(SYSTEM ${GLM_INCLUDE_DIR})

set(TARGET_NAME ${CMAKE_STATIC_LIBRARY_PREFIX}generator${SUFFIX}${CMAKE_STATIC_LIBRARY_SUFFIX})
add_subdirectory(src)
