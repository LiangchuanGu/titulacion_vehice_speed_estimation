cmake_minimum_required(VERSION 2.8)
project(calibrator)


IF(NOT CMAKE_BUILD_TYPE)
  SET(CMAKE_BUILD_TYPE Release)
ENDIF()

MESSAGE("Build type: " ${CMAKE_BUILD_TYPE})

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS}  -Wall  -O3")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall  -std=c++11 -O3")

find_package(OpenCV 4.4.0 REQUIRED PATHS)


include_directories(
${PROJECT_SOURCE_DIR}/src
${OpenCV_INCLUDE_DIRS}
)

set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/lib)

add_executable(
${PROJECT_NAME}
main.cpp
Cfg.cpp
CamCal.cpp
)


target_link_libraries(${PROJECT_NAME}
     ${OpenCV_LIBS}
)
