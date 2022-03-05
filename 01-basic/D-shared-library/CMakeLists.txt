cmake_minimum_required(VERSION 3.22)

project(shared_library)

set(
    hello_library_src
    src/Hello.cpp
)
add_library(
    hello_library
    SHARED
        ${hello_library_src}
)
target_include_directories(
    hello_library
    PUBLIC
        ${PROJECT_SOURCE_DIR}/include
)
add_library(
    hello::library
    ALIAS
        hello_library   
)

add_executable(
    ${PROJECT_NAME}
    src/main.cpp
)
target_link_libraries(
    ${PROJECT_NAME}
    PRIVATE
        hello_library   
)