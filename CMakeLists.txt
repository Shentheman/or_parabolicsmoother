cmake_minimum_required(VERSION 2.8.3)
project(or_parabolicsmoother)

find_package(catkin REQUIRED)
find_package(Boost REQUIRED COMPONENTS chrono system)

###################################
## catkin specific configuration ##
###################################
catkin_package(
  INCLUDE_DIRS include
  LIBRARIES ${PROJECT_NAME}
  CATKIN_DEPENDS
  DEPENDS boost
)

###########
## Build ##
###########

include_directories(
  include/${PROJECT_NAME}
  ${catkin_INCLUDE_DIRS}
  ${Boost_INCLUDE_DIRS}
)

add_executable(mc_test tests/mc_test.cpp)

add_library(${PROJECT_NAME}
  src/DynamicPath.cpp
  src/ParabolicRamp.cpp
  src/Timer.cpp
)
target_link_libraries(${PROJECT_NAME}
  ${catkin_LIBRARIES}
  ${Boost_LIBRARIES}
)


target_link_libraries(mc_test ${PROJECT_NAME})
