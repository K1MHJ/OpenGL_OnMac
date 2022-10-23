set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
cmake_minimum_required(VERSION 3.12)

project(
  OpenGLTuto 
  VERSION 0.1
  DESCRIPTION ""
)

set(CMAKE_CXX_STANDARD 17)
set(GLEW_H /opt/homebrew/Cellar/glew/2.2.0_1/include)
set(GLFW_H /opt/homebrew/Cellar/glfw/3.3.8/include)
set(GLM_H /opt/homebrew/Cellar/glm/0.9.9.8/include)
set(OPENGL_H_DIRS ${GLEW_H} ${GLFW_H} ${GLM_H})
# Add target link
set(GLEW_LINK /opt/homebrew/Cellar/glew/2.2.0_1/lib/libGLEW.2.2.dylib)
set(GLFW_LINK /opt/homebrew/Cellar/glfw/3.3.8/lib/libglfw.3.3.dylib)

# Tutu 1
set(TARGET Tuto01_Exe)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/bin/Tuto01)
file(GLOB_RECURSE SRC_FILES CONFIGURE_DEPENDS
  ${CMAKE_CURRENT_SOURCE_DIR}/Tuto01/*.cpp
)
add_executable(${TARGET} ${SRC_FILES})
target_include_directories(${TARGET} PRIVATE ${OPENGL_H_DIRS})
target_compile_options(${TARGET} PUBLIC -Wall)
target_link_libraries(${TARGET} ${OPENGL} ${GLEW_LINK} ${GLFW_LINK})
target_link_libraries(${TARGET} "-framework OpenGL")
target_link_libraries(${TARGET} "-framework GLUT")

# Tuto 2
set(TARGET Tuto02_Exe)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/bin/Tuto02)
file(GLOB_RECURSE SRC_FILES CONFIGURE_DEPENDS
  ${CMAKE_CURRENT_SOURCE_DIR}/Tuto02/*.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/common/*.cpp
)
add_executable(${TARGET} ${SRC_FILES})
target_include_directories(${TARGET} PRIVATE ${OPENGL_H_DIRS})
target_include_directories(${TARGET} PRIVATE ${CMAKE_CURRENT_SOURCE_DIR})
target_compile_options(${TARGET} PUBLIC -Wall)
target_link_libraries(${TARGET} ${OPENGL} ${GLEW_LINK} ${GLFW_LINK})
target_link_libraries(${TARGET} "-framework OpenGL")
target_link_libraries(${TARGET} "-framework GLUT")
add_custom_command(
  TARGET ${TARGET} POST_BUILD
  COMMAND ${CMAKE_COMMAND} -E copy
  ${CMAKE_CURRENT_SOURCE_DIR}/Tuto02/SimpleVertexShader.vertexshader
  ${CMAKE_CURRENT_SOURCE_DIR}/Tuto02/SimpleFragmentShader.fragmentshader
  ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/
  )

# Tuto 3
set(TARGET Tuto03_Exe)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/bin/Tuto03)
file(GLOB_RECURSE SRC_FILES CONFIGURE_DEPENDS
  ${CMAKE_CURRENT_SOURCE_DIR}/Tuto03/*.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/common/*.cpp
)
add_executable(${TARGET} ${SRC_FILES})
target_include_directories(${TARGET} PRIVATE ${OPENGL_H_DIRS})
target_include_directories(${TARGET} PRIVATE ${CMAKE_CURRENT_SOURCE_DIR})
target_compile_options(${TARGET} PUBLIC -Wall)
target_link_libraries(${TARGET} ${OPENGL} ${GLEW_LINK} ${GLFW_LINK})
target_link_libraries(${TARGET} "-framework OpenGL")
target_link_libraries(${TARGET} "-framework GLUT")
add_custom_command(
  TARGET ${TARGET} POST_BUILD
  COMMAND ${CMAKE_COMMAND} -E copy
  ${CMAKE_CURRENT_SOURCE_DIR}/Tuto03/SimpleTransform.vertexshader
  ${CMAKE_CURRENT_SOURCE_DIR}/Tuto03/SingleColor.fragmentshader
  ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/
  )
