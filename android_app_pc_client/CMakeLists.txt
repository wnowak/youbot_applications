cmake_minimum_required(VERSION 2.8.3)
project(youbot_android)

set(CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/external/cmake_modules")	
find_package(Bluetooth REQUIRED)
find_package(catkin REQUIRED COMPONENTS youbot_driver)

catkin_package(DEPENDS bluez lbluetooth python-bluez lm)

add_definitions(-DYOUBOT_CONFIGURATIONS_DIR="${youbot_driver_CONFIG_DIR}")

include_directories(
	${catkin_INCLUDE_DIRS}
	${BLUETOOTH_INCLUDE_DIR}
)

add_executable(youbot_android
  src/main.cpp
)

target_link_libraries(youbot_android 
	${catkin_LIBRARIES}
	${BLUETOOTH_LIBRARIES}
)


