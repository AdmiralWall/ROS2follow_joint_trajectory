cmake_minimum_required(VERSION 3.5)
project(followjointtrajectory_action_client)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(control_msgs REQUIRED)
find_package(rclcpp REQUIRED)
find_package(rclcpp_action REQUIRED)

add_executable(followjointtrajectory_action_client src/followjointtrajectory_action_client.cpp)
target_include_directories(followjointtrajectory_action_client PUBLIC
"$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>"
  "$<INSTALL_INTERFACE:include>"
${rclcpp_INCLUDE_DIRECTORIES}
${control_msgs_INCLUDE_DIRECTORIES}
)
target_link_libraries(followjointtrajectory_action_client SHARED
${rclcpp_LIBRARIES}
${control_msgs_LIBRARIES}
)

ament_target_dependencies(followjointtrajectory_action_client
  "rclcpp"
  "rclcpp_action"
  "control_msgs")

install(TARGETS
  followjointtrajectory_action_client
  DESTINATION lib/${PROJECT_NAME})

ament_package()
