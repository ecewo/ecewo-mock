cmake_minimum_required(VERSION 3.16)
project(ecewo_mock VERSION 0.1.0 LANGUAGES C)

add_library(ecewo_mock
  src/ecewo-mock.c
)

add_library(ecewo::mock ALIAS ecewo_mock)

target_include_directories(ecewo_mock PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/src>
)

if(TARGET ecewo::ecewo)
    target_link_libraries(ecewo_mock PUBLIC ecewo::ecewo)
else()
