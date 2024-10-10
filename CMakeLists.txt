cmake_minimum_required(VERSION 3.12)

if(${CMAKE_VERSION} VERSION_GREATER_EQUAL "3.27")
    cmake_policy(SET CMP0144 NEW)
endif()

project(qtils LANGUAGES CXX VERSION 0.0.1)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

include(GNUInstallDirs)

find_package(Boost CONFIG REQUIRED)
find_package(fmt CONFIG REQUIRED)

add_library(qtils INTERFACE)
target_link_libraries(qtils INTERFACE
    Boost::boost
    fmt::fmt
)
target_include_directories(qtils INTERFACE
    $<BUILD_INTERFACE:src/qtils>
    $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>
)

install(DIRECTORY src/qtils
    DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
    FILES_MATCHING PATTERN "*.hpp"
)
install(TARGETS qtils EXPORT qtils-config)
install(EXPORT qtils-config
    DESTINATION share/qtils
    NAMESPACE qtils::
)