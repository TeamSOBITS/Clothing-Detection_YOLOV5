cmake_minimum_required(VERSION 3.0.2)
project(clothing_detection)

add_compile_options(-std=c++11)
set(OpenCV_DIR /opt/opencv/opencv_3.4.2/share/OpenCV/)  # for ros melodic
find_package(catkin REQUIRED COMPONENTS
  rospy
  std_msgs
  sensor_msgs
  geometry_msgs
  cv_bridge
)


catkin_package()

find_package(OpenCV 3.4.2 REQUIRED #4.0.0
  NO_MODULE
  PATHS /usr/local
  NO_DEFAULT_PATH
)

include_directories(
  include
  SYSTEM
  ${OpenCV_INCLUDE_DIRS}
  ${PCL_INCLUDE_DIRS}
  ${catkin_INCLUDE_DIRS}
)

