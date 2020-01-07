cmake_minimum_required(VERSION 3.5)

project(02_env)

set(condition "1")

if(DEFINED condition)
message("defined condition")
endif()

#set(ENV{DESTDIR} "./")
if(DEFINED ENV{DESTDIR})
message("defined destdir")
endif()
