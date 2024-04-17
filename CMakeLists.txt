cmake_minimum_required(VERSION 3.28)
project(chromium-cache-viewer)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)


find_package(Qt6 COMPONENTS
        Core
        Gui
        Widgets
        REQUIRED)

add_executable(chromium-cache-viewer main.cpp)
target_link_libraries(chromium-cache-viewer
        Qt::Core
        Qt::Gui
        Qt::Widgets
)

add_custom_command(TARGET chromium-cache-viewer POST_BUILD 
    COMMAND Qt6::windeployqt
    ARGS $<TARGET_FILE:chromium-cache-viewer>
)
