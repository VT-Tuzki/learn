cmake_minimum_required(VERSION 3.10)

# set the project name and version
project(Tutorial VERSION 1.0)

# TODO 4: Replace the following code by:
# * Creating an interface library called tutorial_compiler_flags
#   Hint: use add_library() with the INTERFACE signature
# * Add compiler feature cxx_std_11 to tutorial_compiler_flags
#   Hint: Use target_compile_features()
#新增一个库 tutorial_compiler_flags INTERFACE格式
#无文件 可以根据只要依赖这个库 就会在编译时自动按照这个库的特征来进行编译
#举例特性 c_std_90 c_std_99 c_std_11 c_std_17 c_std_23
add_library(tutorial_compiler_flags INTERFACE)
#设置这个库编译格式为cxx_std_11
target_compile_features(tutorial_compiler_flags INTERFACE cxx_std_11)
# specify the C++ standard

# configure a header file to pass some of the CMake settings
# to the source code
configure_file(TutorialConfig.h.in TutorialConfig.h)

# TODO 2: Remove EXTRA_INCLUDES list

# add the MathFunctions library
add_subdirectory(MathFunctions)

# add the executable
add_executable(Tutorial tutorial.cxx)

# TODO 5: Link Tutorial to tutorial_compiler_flags
#传染特性 包含 tutorial_compiler_flags 的内容都会带上它的特性
target_link_libraries(Tutorial PUBLIC MathFunctions tutorial_compiler_flags)

# TODO 3: Remove use of EXTRA_INCLUDES

# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h
target_include_directories(Tutorial PUBLIC
                           "${PROJECT_BINARY_DIR}"
                           )
