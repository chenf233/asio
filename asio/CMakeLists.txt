cmake_minimum_required(VERSION 3.2)
project(asio)

# 不使用 Boost
add_definitions("-DASIO_STANDALONE")

include_directories(
    ./include
)

# 检查线程支持
find_package(Threads)

add_subdirectory(src/examples/cpp11 examples/cpp11)
