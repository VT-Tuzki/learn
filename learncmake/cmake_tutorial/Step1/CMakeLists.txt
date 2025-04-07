#设置最低可以使用的cmake版本 3.10
cmake_minimum_required(VERSION 3.10)
#设置工程名 Tutorial 版本 1.0
project(Tutorial
    VERSION 1.0)

#设置C++版本 11
set(CMAKE_CXX_STANDARD 11)
#要求使用设置的 CMAKE_CXX_STANDARD版本标准
set(CMAKE_CXX_STANDARD_REQUIRED True)

#将TutorialConfig.h.in 复制并修改为TutorialConfig.h
configure_file(TutorialConfig.h.in TutorialConfig.h)

#添加可执行文件 Tutorial 源于tutorial.cxx
add_executable(Tutorial tutorial.cxx)
#添加对应可执行文件夹的库引用地址 PROJECT_BINARY_DIR
target_include_directories(Tutorial PUBLIC
                            "${PROJECT_BINARY_DIR}"
                            )


#不要随便添加空格