cmake_minimum_required(VERSION 3.20)
project(sourcefs-small-target C CXX)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# ── zlib ──────────────────────────────────────────────────────────────────────
set(ZLIB_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
add_subdirectory(external/zlib)

# ── abseil-cpp ────────────────────────────────────────────────────────────────
set(ABSL_PROPAGATE_CXX_STD ON)
set(BUILD_TESTING OFF CACHE BOOL "" FORCE)
add_subdirectory(external/abseil-cpp)

# ── googletest ────────────────────────────────────────────────────────────────
# Build gtest/gmock libraries only; do not add googletest's own test suite.
set(INSTALL_GTEST OFF CACHE BOOL "" FORCE)
set(gtest_build_tests OFF CACHE BOOL "" FORCE)
set(gmock_build_tests OFF CACHE BOOL "" FORCE)
add_subdirectory(external/googletest)
