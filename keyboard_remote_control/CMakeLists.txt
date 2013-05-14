cmake_minimum_required(VERSION 2.8.3)
project(keyboard_remote_control)

find_package(catkin REQUIRED COMPONENTS youbot_driver)
include_directories(${catkin_INCLUDE_DIRS})
link_directories(${catkin_LIBRARY_DIRS})
catkin_package()

add_definitions(-DYOUBOT_CONFIGURATIONS_DIR="${youbot_driver_CONFIG_DIR}")
add_definitions(-DCONFIG_DIR="${PROJECT_SOURCE_DIR}/config/")

add_executable(youBot_KeyboardRemoteControl
  src/main.cpp
)

target_link_libraries(youBot_KeyboardRemoteControl
	${catkin_LIBRARIES}
	ncurses
)

