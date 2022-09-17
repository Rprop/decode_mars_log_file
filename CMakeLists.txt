cmake_minimum_required (VERSION 3.15)
project (decode_mars_log_file)

# For MSVC
set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")

# For zstd
option(ZSTD_BUILD_STATIC "BUILD STATIC LIBRARIES" ON)
option(ZSTD_BUILD_SHARED "BUILD SHARED LIBRARIES" OFF)
set(ZSTD_SOURCE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/zstd")
set(LIBRARY_DIR ${ZSTD_SOURCE_DIR}/lib)
include(GNUInstallDirs)
add_subdirectory(${CMAKE_SOURCE_DIR}/zstd/build/cmake/lib zstd)

add_executable(decode_mars_log_file
    decode_log_file.c
    micro-ecc-master/uECC.c
    zlib/inflate.c
    zlib/inffast.c
    zlib/adler32.c
    zlib/crc32.c
    zlib/zutil.c
    zlib/inftrees.c
)
target_link_libraries(decode_mars_log_file PRIVATE libzstd_static)
