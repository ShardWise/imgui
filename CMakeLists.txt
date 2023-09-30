
cmake_minimum_required (VERSION 3.8)
project(ImGui VERSION 1.89.8)

set(IMGUI_SOURCES
"imgui_draw.cpp"
"imgui_widgets.cpp"
"imgui.cpp"
"imgui_demo.cpp"
)
set(IMGUI_HEADERS
"imgui.h"
"imconfig.h"
"imgui_internal.h"
"imstb_rectpack.h"
"imstb_textedit.h"
"imstb_truetype.h"
"misc/debuggers/imgui.natvis"
"misc/debuggers/imgui.natstepfilter"
"misc/debuggers/imgui.gdb"
"misc/cpp/imgui_stdlib.h"
"misc/cpp/imgui_stdlib.cpp"
)



add_library(imgui STATIC
"${IMGUI_HEADERS}" "${IMGUI_SOURCES}"
)

target_include_directories(imgui INTERFACE "${CMAKE_CURRENT_SOURCE_DIR}")
target_include_directories(imgui PRIVATE "${CMAKE_CURRENT_SOURCE_DIR}")


if(WIN32)
	set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
endif()

