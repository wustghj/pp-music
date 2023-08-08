# 最小版本号
cmake_minimum_required(VERSION 3.26.1)

# 设置工程名和版本
project(pp-music VERSION 1.0)

# 设置C++11标准
set(CMAKE_CXX_STANDARD 17)

# 这行代码启用了Qt的元对象编译器（MOC）的自动处理，用于生成与信号和槽等Qt特性相关的代码。当启用该选项时，CMake会自动在包含Q_OBJECT宏的Qt头文件上运行moc工具。这是为了确保在Qt中信号和槽机制能够正常工作。
set(CMAKE_AUTOMOC ON)

# 这行代码启用了Qt资源文件的自动处理。在Qt中，资源文件（*.qrc）用于捆绑各种非代码资产，如图像、图标、翻译等。启用CMAKE_AUTORCC告诉CMake自动调用rcc工具，将资源文件编译成可以嵌入到最终可执行文件或库中的二进制格式。
set(CMAKE_AUTORCC ON)

# 这行代码启用了Qt用户界面文件的自动处理。Qt的用户界面文件（*.ui）用于描述应用程序的界面布局。启用CMAKE_AUTOUIC告诉CMake自动调用uic工具，将用户界面文件转换为对应的C++代码。
set(CMAKE_AUTOUIC ON)


# 查找Qt包
find_package(Qt5 COMPONENTS Core Gui Widgets Sql Multimedia REQUIRED)

# 检查是否找到Qt
if(Qt5_FOUND)
    message(STATUS "Found Qt5: ${Qt5_VERSION}")
else()
    message(FATAL_ERROR "Qt5 not found")
endif()

file(GLOB SRC_FILES
    "${PROJECT_SOURCE_DIR}/*")

add_executable(pp-music ${SRC_FILES})


# 链接Qt模块
target_link_libraries(pp-music PRIVATE Qt5::Core Qt5::Gui Qt5::Widgets Qt5::Sql)
