cmake_minimum_required(VERSION 3.22)
project(clock)

set(CMAKE_CXX_STANDARD 14)

add_executable(clock main.cpp)

        include(FetchContent)
    set(BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
    set(BUILD_GAMES OFF CACHE BOOL "" FORCE)
    FetchContent_Declare(raylib GIT_REPOSITORY https://github.com/raysan5/raylib.git GIT_TAG master)
    FetchContent_MakeAvailable(raylib)


    file(GLOB_RECURSE PROJECT_SOURCES CONFIGURE_DEPENDS "${CMAKE_CURRENT_LIST_DIR}/sources/*.c")
    set(PROJECT_INCLUDE "${CMAKE_CURRENT_LIST_DIR}/sources/")


    target_sources(${PROJECT_NAME} PRIVATE ${PROJECT_SOURCES})
    target_include_directories(${PROJECT_NAME} PRIVATE ${PROJECT_INCLUDE})
    target_link_libraries(${PROJECT_NAME} PRIVATE raylib)


    target_compile_definitions(${PROJECT_NAME} PUBLIC ASSETS_PATH="${CMAKE_CURRENT_SOURCE_DIR}/assets/")

