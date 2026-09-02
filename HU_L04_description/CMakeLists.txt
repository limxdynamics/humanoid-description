# Copyright information
#
# © [2025] LimX Dynamics Technology Co., Ltd. All rights reserved.

# Declare the minimum required CMake version
cmake_minimum_required(VERSION 3.10)

# Declare the project
project(HU_L04_description)

set(INSTALL_ROBOT_ASSETS ON)
if(DEFINED ENV{CMAKE_ROBOT_TYPE} AND NOT "$ENV{CMAKE_ROBOT_TYPE}" STREQUAL "")
  set(INSTALL_ROBOT_ASSETS OFF)
  string(TOUPPER "$ENV{CMAKE_ROBOT_TYPE}" CMAKE_ROBOT_TYPE)
  if(CMAKE_ROBOT_TYPE STREQUAL "OLI" AND PROJECT_NAME MATCHES "_D[0-9]+_description$")
    set(INSTALL_ROBOT_ASSETS ON)
  elseif(CMAKE_ROBOT_TYPE STREQUAL "LUNA" AND PROJECT_NAME MATCHES "_L[0-9]+_description$")
    set(INSTALL_ROBOT_ASSETS ON)
  elseif(CMAKE_ROBOT_TYPE STREQUAL "MINI" AND PROJECT_NAME MATCHES "_M[0-9]+_description$")
    set(INSTALL_ROBOT_ASSETS ON)
  endif()
endif()

if(DEFINED ENV{ROS_VERSION})
  if($ENV{ROS_VERSION} EQUAL 1)
    # In ROS1 compilation environment
    message("Currently in ROS1 compilation environment")

    find_package(catkin REQUIRED COMPONENTS roscpp)
    
    catkin_package(CATKIN_DEPENDS)

    # Install directories 'meshes' and 'urdf' to the package share directory
    if(INSTALL_ROBOT_ASSETS)
      install(DIRECTORY meshes urdf xml world DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})
    endif()
  elseif($ENV{ROS_VERSION} EQUAL 2)
    # In ROS2 compilation environment
    message("Currently in ROS2 compilation environment")

    find_package(ament_cmake REQUIRED)

    if(INSTALL_ROBOT_ASSETS)
      install(DIRECTORY meshes urdf xml world DESTINATION share/${PROJECT_NAME})
    endif()

    ament_package()
  else()
    message(WARNING "Unknown ROS version: ${ROS_VERSION}")
  endif()
else()
  if(DEFINED ENV{AMENT_PREFIX_PATH})
    message("Currently is not in ROS compilation environment")
    find_package(ament_cmake REQUIRED)
    if(INSTALL_ROBOT_ASSETS)
      install(DIRECTORY meshes urdf xml world DESTINATION etc/${PROJECT_NAME})
    endif()
    ament_package()
  endif()
endif()