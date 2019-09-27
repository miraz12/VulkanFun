#--------------------------------------------------------------------------
# example project
#--------------------------------------------------------------------------

PROJECT(example)
FILE(GLOB project_headers *.h)
FILE(GLOB project_sources *.cc)

SET(files_project ${project_headers} ${project_sources} )
SOURCE_GROUP("example" FILES ${files_project})




ADD_EXECUTABLE(example ${files_project})

find_package(Vulkan REQUIRED)
add_executable(vulkaninfo vulkaninfo.c)
target_compile_definitions(example PRIVATE VK_USE_PLATFORM_WIN32_KHR)
target_link_libraries(vulkaninfo Vulkan::Vulkan)
ADD_DEPENDENCIES(example glfw glm)
TARGET_LINK_LIBRARIES(example PUBLIC exts glfw glm Vulkan::Vulkan)
IF(MSVC)
	SET_TARGET_PROPERTIES(example PROPERTIES VS_DEBUGGER_WORKING_DIRECTORY "${CMAKE_SOURCE_DIR}")
	set_property(TARGET example PROPERTY CXX_STANDARD 17)
ENDIF()




