
cmake_minimum_required(VERSION 3.22)

project(tests CXX)

set(CMAKE_CXX_STANDARD 17)

add_executable(${PROJECT_NAME} hello_test.cpp)

# Override INSTALL_GTEST in Google test so it puts libraries in our local build directory. 
set(CMAKE_POLICY_DEFAULT_CMP0077 NEW)
set(INSTALL_GTEST OFF)
add_subdirectory("${PROJECT_SOURCE_DIR}/external/googletest" "external/googletest")

target_include_directories(${PROJECT_NAME}
    PUBLIC external/googletest/googletest/include
)
target_link_libraries(${PROJECT_NAME}
    PUBLIC gtest_main
)

