
# Minimum CMake version required
cmake_minimum_required(VERSION 3.0) #

# Project name
project(Argon2) #

# This is the version of C++ that's being used
set(CMAKE_CXX_STANDARD 11) #

# Setting the source files
#set(SOURCE_FILES "${CMAKE_CURRENT_SOURCE_DIR}/src/*.c" "${CMAKE_CURRENT_SOURCE_DIR}/src/*.h")
#set(SOURCE_FILES "src/*.c" "src/*.h")
file (GLOB SOURCEE_FILES "src/*.c") #
file (GLOB BLAKE_FILES "src/blake2/*.c") #
file (GLOB HEADER_FILES "include/argon2.h") #
file (GLOB TESTING_FILES "src/test.c") #

include_directories("include") #
include_directories("kats") #
include_directories("latex") #
include_directories("man") #
include_directories("src") #
include_directories("vs2015") #
include_directories("include/blake2")

file(GLOB ALL_FILES ${SOURCEE_FILES} ${BLAKE_FILES} ${HEADER_FILES}) #

set(testing_files ${ALL_FILES})

list(REMOVE_ITEM testing_files "genkat.c")
list(REMOVE_ITEM testing_files "bench.c")

# Making the executable
add_executable(argon ${testing_files}) #
#add_executable(argon ${TESTING_FILES} ${SOURCEE_FILES})