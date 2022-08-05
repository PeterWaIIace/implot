cmake_minimum_required(VERSION 3.13.0)

project(implot
  LANGUAGES C CXX
)

set(IMPLOT_HEADERS
  "${CMAKE_CURRENT_LIST_DIR}/implot.h"
  "${CMAKE_CURRENT_LIST_DIR}/implot_internal.h"
)

set(IMPLOT_SOURCES
  "${CMAKE_CURRENT_LIST_DIR}/implot.cpp"
  "${CMAKE_CURRENT_LIST_DIR}/implot_items.cpp"
)

add_library(implot INTERFACE)
target_sources(implot INTERFACE
  ${IMPLOT_SOURCES}
  ${IMPLOT_HEADERS}
)
target_include_directories(implot INTERFACE "${CMAKE_CURRENT_LIST_DIR}")
