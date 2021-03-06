cmake_minimum_required (VERSION 3.0)
project(amt)
set(CMAKE_CXX_FLAGS ${CMAKE_CXX_FLAGS} -std=c++17)
SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g -O0")
set(Boost_USE_STATIC_LIBS ON)
find_package(Boost 1.73.0 EXACT REQUIRED COMPONENTS log log_setup filesystem program_options)

include_directories(
    ./
    ${Boost_INCLUDE_DIRS}
)
LINK_DIRECTORIES(/usr/local/lib)

aux_source_directory(./ amt_str)
aux_source_directory(./net amt_str)
aux_source_directory(./log amt_str)
aux_source_directory(./config amt_str)
aux_source_directory(./tool amt_str)

add_executable(amt ${amt_str})
target_link_libraries(amt PRIVATE  ${Boost_LIBRARIES})