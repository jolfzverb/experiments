cmake_minimum_required(VERSION 3.13)

project(hello_user VERSION 1.0.0 DESCRIPTION "Hello world shared library consumer")

set(CMAKE_CXX_FLAGS "-Wall -Werror -pedantic -std=c++1z -O2 -ggdb ${CMAKE_CXX_FLAGS}")

find_package(PkgConfig REQUIRED)
pkg_check_modules(SHARED_HELLO REQUIRED shared_hello)

add_executable(${PROJECT_NAME} ${CMAKE_SOURCE_DIR}/src/main.cpp)

target_link_directories(${PROJECT_NAME} PUBLIC ${SHARED_HELLO_LIBRARY_DIRS})
target_link_libraries(${PROJECT_NAME} ${SHARED_HELLO_LIBRARIES})
target_include_directories(${PROJECT_NAME} PUBLIC ${SHARED_HELLO_INCLUDE_DIRS})
target_compile_options(${PROJECT_NAME} PUBLIC ${SHARED_HELLO_CFLAGS_OTHER})

