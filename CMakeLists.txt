cmake_minimum_required(VERSION 3.16)
project(AlgoAnalytics)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTORCC ON)

find_package(Qt6 COMPONENTS Widgets REQUIRED)

add_executable(AlgoAnalytics
        main.cpp
        mainwindow.cpp
        mainwindow.h
        datastruct.h
        mainwindow.ui
)

target_link_libraries(AlgoAnalytics PRIVATE Qt6::Widgets)