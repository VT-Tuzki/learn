# TODO 14: Remove mysqrt.cxx from the list of sources

# TODO 1: Add a library called MathFunctions with sources MathFunctions.cxx
# and mysqrt.cxx
# Hint: You will need the add_library command
#新增 MathFunctions 库 所包含文件 MathFunctions.cxx
add_library(MathFunctions MathFunctions.cxx)



# TODO 7: Create a variable USE_MYMATH using option and set default to ON
#新增选项 USE_MYMATH 注释  "Use tutorial provided math implementation" 默认开启
#编译时 可以增加 cmake ../Step2 -DUSE_MYMATH=OFF 然后 cmake --build .进行编译
option(USE_MYMATH "Use tutorial provided math implementation" ON)
# TODO 8: If USE_MYMATH is ON, use target_compile_definitions to pass
# USE_MYMATH as a precompiled definition to our source files
if(USE_MYMATH)
    target_compile_definitions(MathFunctions PRIVATE "USE_MYMATH")
    add_library(SqrtLibrary STATIC
            mysqrt.cxx
            )
    target_link_libraries(MathFunctions PRIVATE SqrtLibrary)
endif()
# TODO 12: When USE_MYMATH is ON, add a library for SqrtLibrary with
# source mysqrt.cxx

# TODO 13: When USE_MYMATH is ON, link SqrtLibrary to the MathFunctions Library
