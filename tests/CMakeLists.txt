cmake_minimum_required(VERSION 3.22)

project(tests CXX)

set(CMAKE_CXX_STANDARD 17)

enable_testing()

add_executable(
  hello_test
  hello_test.cpp
)
target_link_libraries(
  hello_test
  gtest_main
)

include(GoogleTest)
gtest_discover_tests(hello_test)


