cmake_minimum_required(VERSION 3.0)

add_library(cpp-feather-ini-parser INTERFACE)
target_sources(cpp-feather-ini-parser INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/INI.h)
target_include_directories(cpp-feather-ini-parser INTERFACE ${CMAKE_CURRENT_SOURCE_DIR})

include(CTest)
if(BUILD_TESTING)
    add_executable(test_cpp_feather_ini_parser ${CMAKE_CURRENT_SOURCE_DIR}/example/example.cpp)
    target_compile_definitions(test_cpp_feather_ini_parser PUBLIC "TESTS_DIR=\"${CMAKE_CURRENT_SOURCE_DIR}/example/\"")
    target_link_libraries(test_cpp_feather_ini_parser PRIVATE cpp-feather-ini-parser)
    add_test(test_cpp_feather_ini_parser test_cpp_feather_ini_parser)
endif()
