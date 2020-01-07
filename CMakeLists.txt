cmake_minimum_required(VERSION 2.8)

project(cecil)

# add preprocess definition
# using : /* #ifdef LICENCE_GEN_TOOL */
add_definitions(-D LICENCE_GEN_TOOL)

# set c++ compile flags
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

# set variable
set(WORKSPAC_DIR ${PROJECT_SOURCE_DIR}/../../../../..)

# header : include directories 
include_directories(${WORKSPAC_DIR}/module/terminal/nl_service/src
                    ${WORKSPAC_DIR}/idl-gen
                    ${WORKSPAC_DIR}/external/inc)


# *.so : dynamic library include directory ( -L)
link_directories(${WORKSPAC_DIR}/module/terminal/nl_service/example/licence_gen_tool_pc/external/lib)

# bin : bin ==> *.cpps 
add_executable(licence_gen_tool_pc src/licence_gen_main.cpp
                    ${WORKSPAC_DIR}/module/terminal/nl_service/src/nlservice_licence.cpp
                    ${WORKSPAC_DIR}/idl-gen/nebulalink.licence.pb.cc
                    )

# bin + *.so : link dynamic library (-l)
target_link_libraries(licence_gen_tool_pc protobuf pthread)

# set variable
set(PORTABLE_TOOL_DIR ${PROJECT_SOURCE_DIR}/portable_tool)

# ***************************************** #
# install (run "make install")
#     PROGRAMS : keep executable permission
# ***************************************** #
install(PROGRAMS build/licence_gen_tool_pc

                DESTINATION ${PORTABLE_TOOL_DIR}/bin
                )

install(PROGRAMS external/lib/libprotobuf.so
                external/lib/libprotobuf.so.11
                external/lib/libprotobuf.so.11.0.0

                DESTINATION ${PORTABLE_TOOL_DIR}/lib
                )
                
install(PROGRAMS makefile/run_licence_gen_tool.sh

                DESTINATION ${PORTABLE_TOOL_DIR}
                )