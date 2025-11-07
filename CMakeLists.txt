cmake_minimum_required(VERSION 3.18)
project(BlackMagicDeckLinkSDK LANGUAGES CXX)

if(APPLE)
    set(TARGET_OS "Mac")
elseif(CMAKE_SYSTEM_NAME STREQUAL "Linux")
    set(TARGET_OS "Linux")
else()
    message(FATAL_ERROR "Unsupported platform: ${CMAKE_SYSTEM_NAME}. CMake does not support this platform.")
endif()

message("Black Magic DeckLink using SDK for Host system: ${TARGET_OS}")

set(SOURCES
    ${TARGET_OS}/include/DeckLinkAPI.h
    ${TARGET_OS}/include/DeckLinkAPIConfiguration.h
    ${TARGET_OS}/include/DeckLinkAPIDeckControl.h
    ${TARGET_OS}/include/DeckLinkAPIDiscovery.h
    ${TARGET_OS}/include/DeckLinkAPIDispatch.cpp
    ${TARGET_OS}/include/DeckLinkAPIModes.h
    ${TARGET_OS}/include/DeckLinkAPITypes.h
    ${TARGET_OS}/include/DeckLinkAPIVersion.h
)

if(TARGET_OS STREQUAL "Linux")
    list(APPEND SOURCES ${TARGET_OS}/include/LinuxCOM.h)
endif()

add_library(${PROJECT_NAME} INTERFACE)
target_sources(${PROJECT_NAME} INTERFACE ${SOURCES})

target_include_directories(${PROJECT_NAME} INTERFACE
    $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/${TARGET_OS}/include/>
    $<INSTALL_INTERFACE:include>
)
