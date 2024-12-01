cmake_minimum_required (VERSION 3.8)

if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

set(CMAKE_CXX_STANDARD 17)

project(xdelta)

add_library(xdelta
    xdelta3/xdelta3.c
)

target_include_directories(xdelta PUBLIC xdelta3)

target_compile_definitions (xdelta PUBLIC XD3_MAIN=0)
target_compile_definitions (xdelta PUBLIC XD3_DEBUG=0)
target_compile_definitions (xdelta PUBLIC XD3_USE_LARGEFILE64=1)
target_compile_definitions (xdelta PUBLIC REGRESSION_TEST=0)
target_compile_definitions (xdelta PUBLIC SECONDARY_DJW=1)
target_compile_definitions (xdelta PUBLIC SECONDARY_FGK=1)
target_compile_definitions (xdelta PUBLIC SIZEOF_SIZE_T=8)
target_compile_definitions (xdelta PUBLIC SIZEOF_UNSIGNED_LONG_LONG=8)
target_compile_definitions (xdelta PUBLIC SECONDARY_LZMA=0)
if (WIN32)
    target_compile_definitions (xdelta PUBLIC XD3_WIN32=1)
endif ()
target_compile_definitions (xdelta PUBLIC EXTERNAL_COMPRESSION=0)
target_compile_definitions (xdelta PUBLIC SHELL_TESTS=0)
target_compile_definitions (xdelta PUBLIC LZMA_API_STATIC)
