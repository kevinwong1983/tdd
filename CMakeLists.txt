cmake_minimum_required(VERSION 3.12)

project(tdd)
set(CMAKE_CXX_STANDARD 14)
set(DCMAKE_C_COMPILER /usr/bin/gcc)
set(DCMAKE_CXX_COMPILER /usr/bin/g++)

# Add Google Test
enable_testing()
find_package(GTest REQUIRED)
include_directories(${GTEST_INCLUDE_DIRS})

find_package(Boost REQUIRED)
find_package(GTest REQUIRED)

file(GLOB_RECURSE SOURCES
    "tdd_template.cpp"
)

add_executable(${PROJECT_NAME} ${SOURCES})

target_link_libraries(${PROJECT_NAME}
    GTest::GTest
    GTest::Main
    gmock_main
    gmock
)

target_include_directories(${PROJECT_NAME} PUBLIC ${Boost_INCLUDE_DIRS} .)

# Enable testing
add_test(NAME ${PROJECT_NAME} COMMAND ${PROJECT_NAME})