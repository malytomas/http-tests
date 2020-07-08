cmake_minimum_required(VERSION 3.10)
project(http-tests CXX C)

# build custom curl
add_subdirectory(src/curl)

# buildsys
include(buildsys/cmake/buildsys.cmake)
list(INSERT CMAKE_MODULE_PATH 0 "${CMAKE_CURRENT_SOURCE_DIR}/modules")

# find boost
find_package(Boost 1.65 REQUIRED
    COMPONENTS thread program_options filesystem system
    date_time serialization regex chrono iostreams)
link_directories(${Boost_LIBRARY_DIRS})
include_directories(SYSTEM ${Boost_INCLUDE_DIRS})

# find curl
find_package(CURL REQUIRED)
include_directories(SYSTEM ${CURL_INCLUDE_DIR})

# modules
add_subdirectory(src/dbglog)
add_subdirectory(src/utility)
add_subdirectory(src/service)
add_subdirectory(src/http)

