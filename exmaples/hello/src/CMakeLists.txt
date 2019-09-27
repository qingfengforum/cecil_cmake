cmake_minimum_required(VERSION 3.5)

aux_source_directory(. DIR_TEST1_SRCS)

#使用 ${DIR_TEST1_SRCS} 这些源文件，生成共享库 test （libTest.a）
add_library(Test ${DIR_TEST1_SRCS})