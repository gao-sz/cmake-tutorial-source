# TODO 1: 设置最小cmake版本要求
cmake_minimum_required(VERSION 3.10)

# 项目名称和版本
project(Tutorial_1 VERSION 2.0)

## 设置C++ std标准
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# TODO 8: Use configure_file to configure and copy TutorialConfig.h.in to
#         TutorialConfig.h
# 增加项目配置文件，configure_file 生成到项目二进制目录
# 所以如果程序要引用生成的TutorialConfig.h 必须将项目二进制目录添加到包含目录列表target_include_directories
configure_file(TutorialConfig.h.in TutorialConfig.h)

# TODO 3: Add an executable called Tutorial to the project
# 可执行程序名称 和项目文件
add_executable(Tutorial tutorial.cxx)



# Hint: Be sure to specify the source file as tutorial.cxx
# 将二进制目录添加到包含目录
target_include_directories(Tutorial PUBLIC
                           "${PROJECT_BINARY_DIR}"
                           )
