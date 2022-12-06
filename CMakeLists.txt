cmake_minimum_required(VERSION 3.15)

project(Qt_demo VERSION 0.1 LANGUAGES CXX)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(OpenCV CONFIG REQUIRED)
find_package(Boost COMPONENTS REQUIRED system)
find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Widgets)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Widgets)

set(PROJECT_SOURCES
        main.cpp
        mainwindow.cpp
        mainwindow.h
        mainwindow.ui
)

add_executable(Qt_demo
    ${PROJECT_SOURCES}
)

target_link_libraries(Qt_demo
        PRIVATE
        opencv_core
        Boost::system
        Qt${QT_VERSION_MAJOR}::Widgets
        )

set_target_properties(Qt_demo PROPERTIES
    WIN32_EXECUTABLE TRUE
)

install(TARGETS Qt_demo
    BUNDLE DESTINATION .
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR})

if(QT_VERSION_MAJOR EQUAL 6)
    qt_finalize_executable(Qt_demo)
endif()
