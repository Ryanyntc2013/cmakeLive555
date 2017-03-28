cmake_minimum_required(VERSION 2.8)

if(POLICY CMP0054)
    cmake_policy(SET CMP0054 NEW)
endif()

aux_source_directory(. SRC_LIST)

list(REMOVE_ITEM SRC_LIST "./openRTSP.cpp")
list(REMOVE_ITEM SRC_LIST "./playCommon.cpp")
list(REMOVE_ITEM SRC_LIST "./playSIP.cpp")
list(REMOVE_ITEM SRC_LIST "./testGSMStreamer.cpp")

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../BasicUsageEnvironment/include)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../groupsock/include)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../liveMedia/include)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../UsageEnvironment/include)
link_directories(${CMAKE_CURRENT_SOURCE_DIR}/../libs)
foreach(src ${SRC_LIST})
    STRING( REGEX REPLACE ".*/(.*)/.cpp$" "/1" prjName ${src} )
    add_executable(${prjName} ${src})
    TARGET_LINK_LIBRARIES(${prjName} ws2_32)
    TARGET_LINK_LIBRARIES(${prjName} libBasicUsageEnvironment libgroupsock libliveMedia libUsageEnvironment)
endforeach(src)

#set(SRC_LIST testRTSPClient.cpp)

#set(prjName testRTSPClient)
#add_executable(${prjName} ${SRC_LIST})

#TARGET_LINK_LIBRARIES(${prjName} ws2_32)
#TARGET_LINK_LIBRARIES(${prjName} libBasicUsageEnvironment libgroupsock libliveMedia libUsageEnvironment)
