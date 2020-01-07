cmake_minimum_required(VERSION 3.0)

project(Cecil_CMake_Install)

#set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/output/bin)

add_executable(t_test main.cpp)

install(TARGETS t_test 
            RUNTIME DESTINATION /home/qf/01_qfCodelib/qf_code/tool/cecil_cmake/exmaples/03_make_install/build/bin)