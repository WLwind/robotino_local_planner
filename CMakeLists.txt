cmake_minimum_required(VERSION 2.8.3)
project(robotino_local_planner)
add_compile_options(-std=c++11)

find_package(catkin REQUIRED  COMPONENTS geometry_msgs tf costmap_2d nav_core nav_msgs pluginlib roscpp std_msgs tf_lookup)

catkin_package(LIBRARIES robotino_local_planner CATKIN_DEPENDS pluginlib roscpp tf tf_lookup)

include_directories(include ${catkin_INCLUDE_DIRS})

add_library(
  RobotinoLocalPlanner 
  src/RobotinoLocalPlanner.cpp )
add_dependencies(RobotinoLocalPlanner ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(RobotinoLocalPlanner ${catkin_LIBRARIES})
