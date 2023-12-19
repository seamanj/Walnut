cmake_minimum_required(VERSION 3.10)
project(Walnut)

find_package(imgui REQUIRED)
set(CMAKE_CXX_STANDARD 17)

add_compile_definitions(WL_PLATFORM_WINDOWS)
# file(GLOB_RECURSE src "Walnut/src/*.cpp" "WalnutApp/src/*.cpp")
file(GLOB_RECURSE src "Walnut/src/*.cpp")

# FOREACH(item ${src})
#   MESSAGE("${item}")
# ENDFOREACH()

list(APPEND CMAKE_PREFIX_PATH "C:\\Program Files (x86)\\GLFW")

find_package(Vulkan REQUIRED)
find_package(glm REQUIRED)
find_package(glfw3 REQUIRED)

set(std_image_dir ${CMAKE_CURRENT_SOURCE_DIR}/vendor/stb_image)
include_directories(${std_image_dir})
include_directories(Walnut/src)


# add_executable(${PROJECT_NAME} ${src})
add_library(${PROJECT_NAME} ${src})
target_include_directories(${PROJECT_NAME} PUBLIC ${Vulkan_INCLUDE_DIRS})
target_link_libraries(${PROJECT_NAME} imgui  glfw ${Vulkan_LIBRARIES} glm::glm)
