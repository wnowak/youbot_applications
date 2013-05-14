cmake_minimum_required(VERSION 2.8.3)
project(hello_world_demo)

find_package(catkin REQUIRED COMPONENTS youbot_driver)
include_directories(${catkin_INCLUDE_DIRS})
link_directories(${catkin_LIBRARY_DIRS})
catkin_package()

add_definitions(-DYOUBOT_CONFIGURATIONS_DIR="${youbot_driver_CONFIG_DIR}")

add_executable(youBot_HelloWorldDemo
  src/main.cpp
)

target_link_libraries(youBot_HelloWorldDemo 
	${catkin_LIBRARIES}
)

OPTION(USE_SETCAP "Set permissions to access ethernet interface without sudo" ON)

SET(SUDO_COMMAND gksudo)
IF($ENV{USE_NORMAL_SUDO})
    SET(SUDO_COMMAND sudo)
ENDIF($ENV{USE_NORMAL_SUDO})

IF(USE_SETCAP)
add_custom_command(TARGET youBot_HelloWorldDemo POST_BUILD
    COMMAND ${SUDO_COMMAND} setcap cap_net_raw+ep $<TARGET_FILE:youBot_HelloWorldDemo>
)    
endif(USE_SETCAP)


install(TARGETS youBot_HelloWorldDemo
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
