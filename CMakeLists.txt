# Disable in-source builds to prevent source tree corruption.
if(" ${CMAKE_SOURCE_DIR}" STREQUAL " ${CMAKE_BINARY_DIR}")
    message(FATAL_ERROR "FATAL: In-source builds are not allowed.")
endif()

cmake_minimum_required(VERSION 3.22)

project(proj CXX)

add_executable(${PROJECT_NAME} main.cpp)

set(CMAKE_CXX_STANDARD 17)

# add_subdirectory(external/opencv)

option(PACKAGE_TESTS "Build the tests" ON)

if(PACKAGE_TESTS)
    enable_testing()
    include(GoogleTest)
    add_subdirectory(tests)
endif()



