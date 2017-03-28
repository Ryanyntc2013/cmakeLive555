project(live555)

cmake_minimum_required(VERSION 2.8)

if(POLICY CMP0054)
    cmake_policy(SET CMP0054 NEW)
endif()

if (NOT DEFINED ${CMAKE_BUILD_TYPE})
    set(CMAKE_BUILD_TYPE "Debug")
endif()

SET(EXECUTABLE_OUTPUT_PATH ${CMAKE_CURRENT_SOURCE_DIR}/bin)
SET(LIBRARY_OUTPUT_PATH ${CMAKE_CURRENT_SOURCE_DIR}/libs)

add_subdirectory(BasicUsageEnvironment)
add_subdirectory(groupsock)
add_subdirectory(liveMedia)
add_subdirectory(UsageEnvironment)
add_subdirectory(testProgs)
