cmake_minimum_required(VERSION 2.8)
cmake_policy(SET CMP0015 NEW)


project(mpc  DESCRIPTION "mpc")


SET(LIB_NAME mpc)

set(CPP_STANDARD_VERSION 17)
set (CMAKE_C_FLAGS ${default_c_flags})
set (CMAKE_CXX_FLAGS ${default_cxx_flags})
set (CMAKE_EXE_LINKER_FLAGS ${default_exe_linker_flags})

# SET(CMAKE_CXX_COMPILER g++)
# SET(CMAKE_C_FLAGS "-std=c++11 -O0 -g -pthread -ggdb2 -Wall -fno-strict-aliasing -rdynamic -fPIC -lrt -E -gdwarf-3")
# SET(CMAKE_CXX_FLAGS "-std=c++11 -O0 -g -pthread -fno-strict-aliasing -Wall -rdynamic -fPIC -lrt")


include_directories(
    D:/lib/eigen-3.4.0
    )


#FILE(GLOB_RECURSE ${LIB_NAME}_src "*.cpp")
set(${LIB_NAME}_src 

    ${CMAKE_CURRENT_SOURCE_DIR}/driver_code.cpp

    ${CMAKE_CURRENT_SOURCE_DIR}/ModelPredictiveController.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ModelPredictiveController.h

 
)

SET(EXECUTABLE_OUTPUT_PATH ./)
ADD_EXECUTABLE(${LIB_NAME}
${${LIB_NAME}_src}
 
)
SET_TARGET_PROPERTIES(${LIB_NAME} PROPERTIES PREFIX "")
TARGET_LINK_LIBRARIES(${LIB_NAME} ${SERVER_LINK_LIBS} -ldl)


 
