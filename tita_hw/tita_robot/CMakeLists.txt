cmake_minimum_required(VERSION 3.10)
project(tita_robot)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Boost REQUIRED COMPONENTS
        system
        filesystem
)

include_directories(
        include
        ${Boost_INCLUDE_DIRS}
)

file(GLOB_RECURSE sources "src/*.cpp")

add_library(${PROJECT_NAME} SHARED ${sources})
target_link_libraries(${PROJECT_NAME} ${Boost_LIBRARIES})


add_executable(test_control test/test.cpp)
target_link_libraries(test_control ${PROJECT_NAME} ${Boost_LIBRARIES})

