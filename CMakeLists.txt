cmake_minimum_required(VERSION 3.8.2)

project(implot
  VERSION 1.82
  LANGUAGES C CXX
)

option(IMPLOT_DEMO "Build implot_demo.cpp" ON)

set(IMPLOT_HEADERS
  "implot.h"
  "implot_internal.h"
)

set(IMPLOT_SOURCES
  "implot.cpp"
  "implot_items.cpp"
)

if(IMPLOT_DEMO)
  list(APPEND IMPLOT_SOURCES "implot_demo.cpp")
endif()

add_library(implot INTERFACE)
target_sources(implot INTERFACE
  ${IMPLOT_SOURCES}
  ${IMPLOT_HEADERS}
)
target_include_directories(implot INTERFACE "${CMAKE_CURRENT_LIST_DIR}")

if(IMPLOT_BACKEND_OPENGL3 AND (NOT CMAKE_SYSTEM_NAME STREQUAL Emscripten))
  add_subdirectory(examples/libs/gl3w)
endif()

add_subdirectory(backends)