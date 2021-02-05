
#  cmake -G"MinGW Makefiles" .. ==> make  (MinGW)
#  camke ..  ==>  cmake --build .   (windows)

cmake_minimum_required(VERSION 3.0)

set(PROJECT_NAME Hello)
project (${PROJECT_NAME})

set (${PROJECT_NAME}_VERSION_MAJOR 1)
set (${PROJECT_NAME}_VERSION_MINOR 0)


set(CMAKE_CXX_COMPILER "gcc")
set(CMAKE_CXX_COMPILER "g++")
set(CMAKE_BUILD_TYPE  "Release")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -pthread")


# 递归列出所有源文件
file (GLOB_RECURSE HEADERS "src/*.h")
file (GLOB_RECURSE SOURCE_FILES "src/*.cpp")

# 打印找到的文件
FOREACH(FILE_PATH ${HEADERS})
    MESSAGE(${FILE_PATH})
    STRING(REGEX REPLACE ".+/(.+)\\..*" "\\1" FILE_NAME ${FILE_PATH})
    MESSAGE(${FILE_NAME})
ENDFOREACH(FILE_PATH)

# 添加一个可编译的目标到工程
add_executable (${PROJECT_NAME} ${SOURCE_FILES})