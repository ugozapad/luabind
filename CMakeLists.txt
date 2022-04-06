cmake_minimum_required(VERSION 3.0 FATAL_ERROR)

project(luabind)

# add lua project
add_subdirectory(lua)

set(LUABIND_PATH "${CMAKE_CURRENT_SOURCE_DIR}/luabind")

file(GLOB LUABIND_SRC
	"${LUABIND_PATH}/*.cpp"
	"${LUABIND_PATH}/*.hpp"
)

file(GLOB LUABIND_DETAIL_SRC
	"${LUABIND_PATH}/detail/*.cpp"
	"${LUABIND_PATH}/detail/*.hpp"
)

source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} FILES ${LUABIND_SRC})
source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} FILES ${LUABIND_DETAIL_SRC})

add_library(luabind STATIC
	${LUABIND_SRC}
	${LUABIND_DETAIL_SRC}
)

target_include_directories(luabind PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}")
target_link_libraries(luabind lua)