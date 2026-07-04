cmake_minimum_required(VERSION 3.8)
project(topic_converter)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(nav_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(tf2_ros REQUIRED)

add_executable(odom_to_tf_node
  src/topic_converter_node.cpp
)

ament_target_dependencies(odom_to_tf_node
  rclcpp
  nav_msgs
  geometry_msgs
  tf2_ros
)

install(TARGETS
  odom_to_tf_node
  DESTINATION lib/${PROJECT_NAME}
)

ament_package()
