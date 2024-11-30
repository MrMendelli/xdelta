cmake_minimum_required (VERSION 3.8)

if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

set(CMAKE_CXX_STANDARD 17)

add_compile_definitions (XD3_MAIN=0)
add_compile_definitions (XD3_DEBUG=0)
add_compile_definitions (XD3_USE_LARGEFILE64=1)
add_compile_definitions (REGRESSION_TEST=0)
add_compile_definitions (SECONDARY_DJW=1)
add_compile_definitions (SECONDARY_FGK=1)
add_compile_definitions (SIZEOF_SIZE_T=8)
add_compile_definitions (SIZEOF_UNSIGNED_LONG_LONG=8)
add_compile_definitions (SECONDARY_LZMA=0)
if (WIN32)
    add_compile_definitions (XD3_WIN32=1)
endif ()
add_compile_definitions (EXTERNAL_COMPRESSION=0)
add_compile_definitions (SHELL_TESTS=0)
add_compile_definitions (LZMA_API_STATIC)

project(xdelta)

add_library(xdelta
    xdelta3/xdelta3.c
)
