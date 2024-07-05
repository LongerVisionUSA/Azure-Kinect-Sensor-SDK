# Copyright (c) Microsoft Corporation. All rights reserved.
# Licensed under the MIT License.

find_package(OpenGL REQUIRED)
find_package(glfw3 REQUIRED)
find_package(gl3w REQUIRED)
find_package(imgui REQUIRED)
include_directories(
    .
    ${OPENGL_INCLUDE_DIRS}
)

add_executable(viewer_opengl
    main.cpp
    texture.cpp
    viewerwindow.cpp)

target_link_libraries(viewer_opengl PRIVATE
    k4a::k4a
    gl3w
    glfw
    imgui
    imgui_backends
    ${OPENGL_LIBRARIES})
