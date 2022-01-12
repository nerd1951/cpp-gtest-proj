
cmake_minimum_required(VERSION 3.22)

if(POLICY CMP0077)
  cmake_policy(SET CMP0077 NEW)  # CMake 3.13+: option() honors normal variables.
endif()

project(tests CXX)

set(CMAKE_CXX_STANDARD 17)

add_executable(${PROJECT_NAME} hello_test.cpp)

# Override INSTALL_GTEST to create Google test libraries in the build directory. 
set(INSTALL_GTEST OFF)

add_subdirectory("${PROJECT_SOURCE_DIR}/external/googletest" "external/googletest")

target_include_directories(${PROJECT_NAME}
    PUBLIC external/googletest/googletest/include
)
target_link_libraries(${PROJECT_NAME}
    PUBLIC gtest_main
)

