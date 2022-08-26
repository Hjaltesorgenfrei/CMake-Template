cmake_minimum_required(VERSION 3.14)
set(CMAKE_CXX_STANDARD 20)
project (Template_Project)

if(MSVC)
    set(build-output-path ${CMAKE_BINARY_DIR}/${CMAKE_BUILD_TYPE_INIT})
else()
    set(build-output-path ${CMAKE_BINARY_DIR})
endif()

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

add_subdirectory(shared)
add_subdirectory(main)
add_subdirectory(tests)
