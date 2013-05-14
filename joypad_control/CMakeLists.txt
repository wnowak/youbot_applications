cmake_minimum_required(VERSION 2.8.3)
project(joypad_control)

find_package(catkin REQUIRED COMPONENTS youbot_driver)
include_directories(${catkin_INCLUDE_DIRS})
link_directories(${catkin_LIBRARY_DIRS})
catkin_package()

add_definitions(-DYOUBOT_CONFIGURATIONS_DIR="${youbot_driver_CONFIG_DIR}")
add_definitions(-DCONFIG_DIR="${PROJECT_SOURCE_DIR}/config/")

add_executable(youBot_JoypadControl
  src/main.cpp
  src/YouBotJoypad.cpp
  src/YouBotJoypad.hpp
  src/main.cpp
)

target_link_libraries(youBot_JoypadControl
	${catkin_LIBRARIES}
	SDL
)

