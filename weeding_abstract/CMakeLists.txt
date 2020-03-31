cmake_minimum_required(VERSION 2.8.3)
project(weeding_abstract)

## Find CATKIN macros and libraries
## if COMPONENTS list like find_package(CATKIN REQUIRED COMPONENTS xyz)
## is used, also find other CATKIN packages
find_package(catkin REQUIRED COMPONENTS
  roscpp
)

###################################
## CATKIN specific configuration ##
###################################
## The CATKIN_package macro generates cmake config files for your package
## Declare things to be passed to dependent projects
## INCLUDE_DIRS: uncomment this if you package contains header files
## LIBRARIES: libraries you create in this project that dependent projects also need
## CATKIN_DEPENDS: CATKIN_packages dependent projects also need
## DEPENDS: system dependencies of this project that dependent projects also need
catkin_package(
  INCLUDE_DIRS
    include
  LIBRARIES
    weeding_abstract
  CATKIN_DEPENDS
    roscpp
)

###########
## Build ##
###########

## Specify additional locations of header files
## Your package locations should be listed before other locations
# include_directories(include)
include_directories(
  include
  ${catkin_INCLUDE_DIRS}
  ${Eigen_INCLUDE_DIRS}
)

## Declare a C++ library
add_library(
  weeding_abstract
  src/abstract_arm_ros_interface.cpp
)
target_link_libraries(weeding_abstract ${catkin_LIBRARIES})

if(CATKIN_EXPORTED_LIBRARIES)
  add_dependencies(weeding_abstract ${CATKIN_EXPORTED_LIBRARIES})
endif()
