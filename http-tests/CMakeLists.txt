cmake_minimum_required(VERSION 3.10)
project(http-tests CXX C)
include(buildsys/cmake/buildsys.cmake)

# find 3rd party dependencies
find_package(Boost 1.65 REQUIRED
    COMPONENTS thread program_options filesystem system
    date_time serialization regex chrono iostreams)
link_directories(${Boost_LIBRARY_DIRS})
include_directories(SYSTEM ${Boost_INCLUDE_DIRS})
find_package(CURL REQUIRED)
include_directories(SYSTEM ${CURL_INCLUDE_DIR})
    
# modules
add_subdirectory(src/dbglog)
add_subdirectory(src/utility)
add_subdirectory(src/service)
add_subdirectory(src/http)

