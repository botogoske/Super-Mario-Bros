cmake_minimum_required(VERSION 3.10)
project(SuperMarioBros CXX)
set(CMAKE_CXX_STANDARD_REQUIRED True)
set(CMAKE_CXX_STANDARD 17)

set(SOURCES 
    Source/Animation.cpp
    Source/ConvertSketch.cpp
    Source/DrawMap.cpp
    Source/Enemy.cpp
    Source/Goomba.cpp
    Source/Koopa.cpp
    Source/Main.cpp
    Source/MapCollision.cpp
    Source/MapManager.cpp
    Source/Mario.cpp
    Source/Mushroom.cpp
)

set (HEADERS_DIR ${CMAKE_CURRENT_SOURCE_DIR}/Headers/)

set(CMAKE_NO_SYSTEM_FROM_IMPORTED ON)
find_package(SFML 3.0.2 COMPONENTS Graphics Audio REQUIRED)

add_executable(mario ${SOURCES})
target_include_directories(mario PRIVATE ${HEADERS_DIR})
target_link_libraries(mario SFML::Graphics SFML::Audio)

add_custom_command(TARGET mario POST_BUILD
                   COMMAND "${CMAKE_COMMAND}" -E copy_directory "${CMAKE_SOURCE_DIR}/Source/Resources" "${CMAKE_BINARY_DIR}/Resources")
