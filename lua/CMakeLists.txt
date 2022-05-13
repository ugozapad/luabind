file(GLOB LUA_SRC
	"${CMAKE_CURRENT_SOURCE_DIR}/src/*.c"
	"${CMAKE_CURRENT_SOURCE_DIR}/src/*.h"
)

list(REMOVE_ITEM LUA_SRC "${CMAKE_CURRENT_SOURCE_DIR}/src/lua.c")
list(REMOVE_ITEM LUA_SRC "${CMAKE_CURRENT_SOURCE_DIR}/src/luac.c")

add_library(lua STATIC ${LUA_SRC})
target_include_directories(lua PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/src")