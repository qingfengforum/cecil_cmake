# cmake by qf
----
`<source files> ==generate rules==> <traget files>`

### source files
```
xxx.h
xxx.cpp
libxxx.so

<self_defined>
```
### source directories
```
include directories
```
### set
```
- compile flags
- output folder
```


### basic syntax
```cmake
cmake_minimum_required(VERSION 2.8)

project(CWAVE_NL)

# .... others
```

### variables
```json
[CMAKE_SOURCE_DIR] : The path to the top level of the source tree.
[PROJECT_SOURCE_DIR] : Top level source directory for the current project.
```

### command
```cmake
#Load and run CMake code from a file or module.
include(${CMAKE_SOURCE_DIR}/cmake/rule/ConfigureTarget.cmake)

#Provides an option that the user can optionally select.
option(DTT_PLATFORM "DTT Platform" OFF)

#Add a subdirectory to the build.
add_subdirectory(idl)

#Add include directories to the build.
include_directories(${CMAKE_SOURCE_DIR}/base_core/V2XCommonBase)
#Specify directories in which the linker will look for libraries.
link_directories(${CMAKE_SOURCE_DIR}/output/public/lib)
```

### cmake configure
```cmake
#Start recording a macro for later invocation as a command::
macro(ConfigureTarget TARGET_NAME)
#Ends a list of commands in a macro block.
endmacro(ConfigureTarget TARGET_NAME)

#Targets can have properties that affect how they are built.
set_target_properties(${TARGET_NAME} PROPERTIES
    ARCHIVE_OUTPUT_DIRECTORY "${PROJECT_SOURCE_DIR}/output/lib"
    LIBRARY_OUTPUT_DIRECTORY "${PROJECT_SOURCE_DIR}/output/lib"
    RUNTIME_OUTPUT_DIRECTORY "${PROJECT_SOURCE_DIR}/output/bin"
)

#File manipulation command.
#Generate a list of files that match the <globbing-expressions> and store it into the <variable>. 
file(GLOB output_files ${PROJECT_SOURCE_DIR}/output/*)
#The COPY signature copies files, directories, and symlinks to a destination folder.
file(COPY ${output_files} DESTINATION ${CMAKE_SOURCE_DIR}/output/module/${TARGET_NAME})

#if : Conditionally execute a group of commands.
#DEFINED{ARCH} : To test whether an environment variable is defined, use the signature if(DEFINED ENV{<name>}) of the if() command.
#set ENV : Sets an Environment Variable to the given value. Subsequent calls of $ENV{<variable>} will return this new value.
set(ENV{<variable>} [<value>])
if(DEFINED ENV{ARCH})
endif()
```