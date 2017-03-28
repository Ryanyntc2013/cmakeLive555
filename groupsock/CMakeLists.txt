aux_source_directory(. SRC_LIST)
ADD_LIBRARY(libgroupsock ${SRC_LIST})

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../BasicUsageEnvironment/include)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../groupsock/include)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../liveMedia/include)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../UsageEnvironment/include)
include_directories(${CMAKE_CURRENT_SOURCE_DIR})

if (WIN32)

else()
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -g")
endif()
