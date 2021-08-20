cmake_minimum_required(VERSION 3.16)
project(TinyWebServer)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_EXTENSIONS ON)
set(CMAKE_CXX_STANDARD_REQUIRED OFF)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -pthread")
message("C++ compiler flags: ${CMAKE_CXX_FLAGS}")
message(aaa)

#指定编译选项
set(CMAKE_BUILD_TYPE Debug )
#指定编译目录
#set(PROJECT_BINARY_DIR ${PROJECT_SOURCE_DIR}/build)
find_library(MYSQL_LIB mysqlclient)

#指定头文件目录,PROJECT_SOURCE_DIR为工程的根目录
include_directories(${PROJECT_SOURCE_DIR}/include)
##指定源文件路径
aux_source_directory(./src SRC)
#指定可执行文件的输出目录，输出到bin下面
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
#指定生成目标
add_executable(main main.cpp ${SRC})
target_link_libraries(main ${MYSQL_LIB})