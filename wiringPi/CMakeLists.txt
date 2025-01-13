cmake_minimum_required(VERSION 3.30)

file(GLOB SRC "*.[ch]")

project(wiringPi)
add_library(wiringPi SHARED ${SRC})

target_sources(wiringPi PRIVATE ${SRC})

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -D_GNU_SOURCE -O2 -Wformat=2 -Wall -Wextra -Winline -I. -pipe -fPIC ${ExtraFlags}")
set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} ${ExtraFlags}")
set(CMAKE_SHARED_LINKER_FLAGS "${CMAKE_SHARED_LINKER_FLAGS} ${ExtraFlags}")

target_link_libraries(wiringPi "m")
target_link_libraries(wiringPi "pthread")
target_link_libraries(wiringPi "rt")
