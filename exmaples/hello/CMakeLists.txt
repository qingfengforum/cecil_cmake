CMAKE_MINIMUM_REQUIRED (VERSION 3.2) # minimum version required

project(HELLO) # project name

add_subdirectory(src)

aux_source_directory(. DIR_SRCS) 

add_executable(hello ${DIR_SRCS})

#指明 可执行文件hello 需要链接一个名为Test的链接库
target_link_libraries(hello Test)



