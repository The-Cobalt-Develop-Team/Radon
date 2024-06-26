cmake_minimum_required(VERSION 3.16.3)

project(Radon)

# Compile options
set(CMAKE_C_COMPILER "gcc")
set(CMAKE_CXX_COMPILER "g++")
set(CMAKE_BUILD_TYPE DEBUG)
set(CMAKE_CXX_FLAGS "-fno-asm -std=c++14 -Wall")
set(CMAKE_CXX_FLAGS_DEBUG "-g -Og")
set(CMAKE_CXX_FLAGS_RELEASE "-O2")
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/lib)

# Show message
message("cdg2.0release -- A data generator based on C++")
if(${CMAKE_BUILD_TYPE} STREQUAL DEBUG)
    message("Optional:-fno-asm -std=c++11 -Wall -stdlib=libstdc++ -g -Og, Type:Debug")
else(${CMAKE_BUILD_TYPE} STREQUAL RELEASE)
    message("Optional:-fno-asm -std=c++11 -Wall -stdlib=libstdc++ -O2, Type:Release")
endif(${CMAKE_BUILD_TYPE} STREQUAL DEBUG)

include_directories(include)
include_directories(include/Graph)
add_subdirectory(src)

# Install options

# Library
#install(TARGETS 
#        ARCHIVE DESTINATION lib)

# Header files
install(DIRECTORY ${PROJECT_SOURCE_DIR}/include/
        DESTINATION include)

# Executable files
install(TARGETS radon
        RUNTIME DESTINATION bin)

# add_executable(treeTest test/treeTest.cpp)
# add_executable(digraphTest test/digraphTest.cpp)