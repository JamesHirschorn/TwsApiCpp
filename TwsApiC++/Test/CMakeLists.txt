cmake_minimum_required(VERSION 3.1.0)

project(TWSAPICPP_TEST VERSION 1.0.0)

# Load the TwsCppApi dependency.
find_package(TwsApiCpp 9.71.0)

set(SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/Src)

add_definitions(-D_REENTRANT)

set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)

#include_directories(${API_INCLUDE_DIR} ${IB_POSIX_CLIENT_INCLUDE_DIR})

add_executable(Test ${SOURCE_DIR}/Test.cpp)
# This adds everything needed for the TwsCppApi dependency: include 
# directories, compiler definitions, library location, etc...
target_link_libraries(Test TwsCppApi Threads::Threads)
target_compile_options(Test PRIVATE -Wall)

add_executable(History ${SOURCE_DIR}/History.cpp)
target_link_libraries(History TwsCppApi Threads::Threads)
target_compile_options(History PRIVATE -Wall)

add_executable(Bars ${SOURCE_DIR}/Bars.cpp)
target_link_libraries(Bars TwsCppApi Threads::Threads)
target_compile_options(Bars PRIVATE -Wall)

add_executable(Clients ${SOURCE_DIR}/Clients.cpp)
target_link_libraries(Clients TwsCppApi Threads::Threads)
target_compile_options(Clients PRIVATE -Wall)