cmake_minimum_required(VERSION 2.8)

project(shared_hello)

set(CMAKE_C_FLAGS "-Wall -Werror -pedantic -std=c1z -O2 -fsanitize=address ${CMAKE_C_FLAGS}")
set(CMAKE_CXX_FLAGS "-Wall -Werror -pedantic -std=c++1z -O2 -fsanitize=address ${CMAKE_CXX_FLAGS}")

include_directories(${CMAKE_SOURCE_DIR})

add_library(shared_hello SHARED ${CMAKE_SOURCE_DIR}/src/hello.cpp)

