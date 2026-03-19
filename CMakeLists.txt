cmake_minimum_required(VERSION 3.20)

project(imvideostreamer)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

add_executable(imvideo
    src/main.cpp

    # imgui core
    external/imgui/imgui.cpp
    external/imgui/imgui_demo.cpp
    external/imgui/imgui_draw.cpp
    external/imgui/imgui_tables.cpp
    external/imgui/imgui_widgets.cpp

    # imgui backend
    external/imgui/backends/imgui_impl_opengl3.cpp
    external/imgui/backends/imgui_impl_glfw.cpp
)

target_include_directories(imvideo PRIVATE
    external/imgui
    external/imgui/backends
)

target_link_libraries(imvideo PRIVATE
    glfw
    GL
    avcodec
    avutil
    avformat
    swscale
)