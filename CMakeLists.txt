cmake_minimum_required(VERSION 2.8)
project(miniftp-conf)

set(CMAKE_CXX_STANDARD 11)

set(SOURCE_FILES
        common.h
        parseconf.c
        parseconf.h
        str.c
        str.h
        tunable.c
        tunable.h
        main.c)

add_executable(miniftp-conf ${SOURCE_FILES})
