cmake_minimum_required(VERSION 2.8.3)
project(p3at_gazebo)

find_package(catkin REQUIRED COMPONENTS geometry_msgs sensor_msgs std_msgs tf urdf kdl_parser)

catkin_package(
    CATKIN_DEPENDS tf urdf geometry_msgs sensor_msgs std_msgs kdl_parser
)

include_directories(
  ${catkin_INCLUDE_DIRS}
)

set(CMAKE_CXX_FLAGS "-std=c++11")

add_executable(p2os_publisher src/publisher.cc)
target_link_libraries(p2os_publisher ${catkin_LIBRARIES})

install(TARGETS p2os_publisher
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

add_executable(p2os_publisher_3at src/publisher3at.cc)
target_link_libraries(p2os_publisher_3at ${catkin_LIBRARIES})

install(TARGETS p2os_publisher_3at 
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install(DIRECTORY 
   launch defs meshes models
   DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
 )
