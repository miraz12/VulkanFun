#--------------------------------------------------------------------------
# exts
#--------------------------------------------------------------------------

ADD_LIBRARY(exts INTERFACE)

SET(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "Build the GLFW example programs")
SET(GLFW_BUILD_TESTS OFF CACHE BOOL "Build the GLFW test programs")
SET(GLFW_BUILD_DOCS OFF CACHE BOOL "Build the GLFW documentation")
SET(GLFW_INSTALL OFF CACHE BOOL "Generate installation target")		  

ADD_SUBDIRECTORY(glfw-3.2.1)
SET_TARGET_PROPERTIES(glfw PROPERTIES FOLDER "exts/glfw")
TARGET_INCLUDE_DIRECTORIES(exts INTERFACE glfw-3.2.1/include)

ADD_SUBDIRECTORY(glm)
TARGET_LINK_LIBRARIES(exts INTERFACE )
