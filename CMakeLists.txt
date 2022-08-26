cmake_minimum_required(VERSION 3.14)
set(CMAKE_CXX_STANDARD 20)
project (Template_Project)

include(FetchContent) 
FetchContent_Declare(
    fmt                   #name of repository
    GIT_REPOSITORY https://github.com/fmtlib/fmt
    GIT_TAG        9.0.0
)

FetchContent_MakeAvailable(fmt)

file(GLOB_RECURSE SOURCES CONFIGURE_DEPENDS "src/*.cpp")

add_executable(${CMAKE_PROJECT_NAME} ${SOURCES}) 
target_link_libraries(${CMAKE_PROJECT_NAME} PRIVATE fmt)

if(MSVC)
    set(build-output-path ${CMAKE_BINARY_DIR}/${CMAKE_BUILD_TYPE_INIT})
    target_compile_options(${CMAKE_PROJECT_NAME} PRIVATE /W4 /WX)
else()
    target_compile_options(${CMAKE_PROJECT_NAME} PRIVATE -Wall -Wextra -Wpedantic -Werror)
    set(build-output-path ${CMAKE_BINARY_DIR})
endif()
