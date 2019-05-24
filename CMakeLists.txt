cmake_minimum_required(VERSION 2.8)

###################################################################################
project(RapidHttpTest)

if (CMAKE_BUILD_TYPE)
else()
    #set(CMAKE_BUILD_TYPE DEBUG)
    set(CMAKE_BUILD_TYPE RELEASE)
endif()

set(CMAKE_CXX_FLAGS "-std=c++11 -g -Wall")

option(WITH_PROFILE "link benchmark with profiler" OFF)
message("------------ Options -------------")
message("  CMAKE_BUILD_TYPE: ${CMAKE_BUILD_TYPE}")
message("  CMAKE_CXX_FLAGS_FINAL: ${CMAKE_CXX_FLAGS_${CMAKE_BUILD_TYPE}}")
message("  WITH_PROFILE: ${WITH_PROFILE}")

configure_file(${PROJECT_SOURCE_DIR}/include/rapidhttp/cmake_config.h.in ${PROJECT_SOURCE_DIR}/include/rapidhttp/cmake_config.h)

include_directories("${PROJECT_SOURCE_DIR}/include")
install(DIRECTORY ${PROJECT_SOURCE_DIR}/include/rapidhttp DESTINATION "include" FILES_MATCHING PATTERN "*.*")
