cmake_minimum_required(VERSION 3.13.0)

project(implot
  VERSION 1.82
  LANGUAGES C CXX
)

option(IMPLOT_DEMO "Build implot_demo.cpp" ON)

set(IMPLOT_HEADERS
  "${CMAKE_CURRENT_LIST_DIR}/implot.h"
  "${CMAKE_CURRENT_LIST_DIR}/implot_internal.h"
)

set(IMPLOT_SOURCES
  "${CMAKE_CURRENT_LIST_DIR}/implot.cpp"
  "${CMAKE_CURRENT_LIST_DIR}/implot_items.cpp"
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
