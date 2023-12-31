cmake_minimum_required(VERSION 3.9)
project(Communication)

set(CMAKE_CXX_COMPILER "g++")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -std=c++14")

add_executable(Server
    Lib/Exception.cpp
    Lib/Curl.cpp
    Lib/StringOperation.cpp
    Server.cpp)
add_executable(Client
    Lib/Exception.cpp
    Lib/Curl.cpp
    Lib/StringOperation.cpp
    Client.cpp)
target_include_directories(Server PUBLIC Lib)
target_include_directories(Client PUBLIC Lib)

find_library(LIBCURL curl REQUIRED)
find_library(LIBPTHREAD pthread REQUIRED)
set(LIBS
    ${LIBCURL}
    ${LIBPTHREAD}
)
target_link_libraries(Server PRIVATE ${LIBS})
target_link_libraries(Client PRIVATE ${LIBS})
