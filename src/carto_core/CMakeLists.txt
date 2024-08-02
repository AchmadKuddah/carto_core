cmake_minimum_required(VERSION 2.8.3)
project(carto_core)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  roslib
  cartographer_ros
  geometry_msgs
  rospy
  sensor_msgs
  std_msgs
  std_srvs
  tf
)

find_package(cartographer REQUIRED)
include("${CARTOGRAPHER_CMAKE_DIR}/functions.cmake")

catkin_package(
#  INCLUDE_DIRS include
  LIBRARIES carto_core
  CATKIN_DEPENDS roscpp
  DEPENDS system_lib
)

install(DIRECTORY launch configuration_files param urdf
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)

# header files
install(DIRECTORY include/${PROJECT_NAME}/
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
  FILES_MATCHING PATTERN "*.h"
)