cmake_minimum_required(VERSION 2.8.3)
project(youbot_joint_configurator)
find_package(catkin REQUIRED COMPONENTS youbot_driver)


include_directories(${catkin_INCLUDE_DIRS})

link_directories(${catkin_LIBRARY_DIRS})
catkin_package(
	INCLUDE_DIRS ${INCLUDE_DIRS} 
)

IF(NOT DEFINED JOINT_CONFIGURATOR_CONFIG_DIR)
  SET(JOINT_CONFIGURATOR_CONFIG_DIR ${PROJECT_SOURCE_DIR}/config/)
ENDIF(NOT DEFINED JOINT_CONFIGURATOR_CONFIG_DIR)

SET(YOUBOT_DRIVER_CONFIG
${PROJECT_SOURCE_DIR}/config/arm-1.cfg
${PROJECT_SOURCE_DIR}/config/arm-2.cfg
${PROJECT_SOURCE_DIR}/config/arm-3.cfg
${PROJECT_SOURCE_DIR}/config/arm-4.cfg
${PROJECT_SOURCE_DIR}/config/arm-5.cfg
${PROJECT_SOURCE_DIR}/config/arm-1-protected.cfg
${PROJECT_SOURCE_DIR}/config/arm-2-protected.cfg
${PROJECT_SOURCE_DIR}/config/arm-3-protected.cfg
${PROJECT_SOURCE_DIR}/config/arm-4-protected.cfg
${PROJECT_SOURCE_DIR}/config/arm-5-protected.cfg
${PROJECT_SOURCE_DIR}/config/base.cfg
${PROJECT_SOURCE_DIR}/config/base-protected.cfg
)

add_definitions(-DCONFIG_DIR="${JOINT_CONFIGURATOR_CONFIG_DIR}")

add_definitions(-DYOUBOT_CONFIGURATIONS_DIR="${youbot_driver_CONFIG_DIR}")

add_definitions(youbot_joint_configurator
  src/JointConfiguratorMain.cpp
)

add_executable(youbot_arm_configurator
  src/ArmConfigurator.cpp
)

add_executable(youbot_base_configurator
  src/BaseConfigurator.cpp
)

add_library(joint_configurator
  src/JointConfigurator.cpp
)

target_link_libraries(youbot_joint_configurator 
	${catkin_LIBRARIES}
	joint_configurator
)

target_link_libraries(youbot_arm_configurator 
	${catkin_LIBRARIES}
	joint_configurator
)

target_link_libraries(youbot_base_configurator 
	${catkin_LIBRARIES}
	joint_configurator
)

install(TARGETS youbot_joint_configurator youbot_arm_configurator youbot_base_configurator 
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

