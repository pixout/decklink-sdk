cmake_minimum_required(VERSION 3.18)
project(BlackMagicDeckLinkSDK LANGUAGES CXX)

if(APPLE)
    set(TARGET_OS "macOS")
elseif(UNIX)
    set(TARGET_OS "Linux")
else()
    set(TARGET_OS ${CMAKE_SYSTEM_NAME})
endif()

message("Black Magic DeckLink using SDK for Host system: ${TARGET_OS}")

if(APPLE)
    #TBD
elseif(WIN32)
    #TBD
elseif(UNIX AND NOT APPLE)

    set(SOURCES
        ${TARGET_OS}/include/DeckLinkAPI.h
        ${TARGET_OS}/include/DeckLinkAPIConfiguration.h
        ${TARGET_OS}/include/DeckLinkAPIDeckControl.h
        ${TARGET_OS}/include/DeckLinkAPIDiscovery.h
        ${TARGET_OS}/include/DeckLinkAPIDispatch.cpp
        ${TARGET_OS}/include/DeckLinkAPIModes.h
        ${TARGET_OS}/include/DeckLinkAPITypes.h
        ${TARGET_OS}/include/DeckLinkAPIVersion.h
        ${TARGET_OS}/include/LinuxCOM.h
    )

endif()

add_library(${PROJECT_NAME} INTERFACE)
target_sources(${PROJECT_NAME} INTERFACE ${SOURCES})

target_include_directories(${PROJECT_NAME} INTERFACE
    $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/${TARGET_OS}/include/>
    $<INSTALL_INTERFACE:include>
)
