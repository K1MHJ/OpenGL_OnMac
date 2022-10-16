cmake_minimum_required(VERSION 3.12)

project(OpenGLTuto)

set(CMAKE_CXX_STANDARD 17)

set(GLEW_H /opt/homebrew/Cellar/glew/2.2.0_1/include)
set(GLFW_H /opt/homebrew/Cellar/glfw/3.3.8/include)
set(GLM_H /opt/homebrew/Cellar/glm/0.9.9.8/include)

include_directories(${GLEW_H} ${GLFW_H} ${GLM_H} )

# Add target link
set(GLEW_LINK /opt/homebrew/Cellar/glew/2.2.0_1/lib/libGLEW.2.2.dylib)
set(GLFW_LINK /opt/homebrew/Cellar/glfw/3.3.8/lib/libglfw.3.3.dylib)
link_libraries(${OPENGL} ${GLEW_LINK} ${GLFW_LINK})

# Execute compile command
set(SRC_FILES main.cpp)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
add_executable(OpenGLTest ${SRC_FILES})

# mac, it's important to take this step
target_link_libraries(OpenGLTest "-framework OpenGL")
target_link_libraries(OpenGLTest "-framework GLUT")
