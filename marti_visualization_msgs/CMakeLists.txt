cmake_minimum_required(VERSION 3.5)
project(marti_visualization_msgs)

# Add support for C++11
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 11)
endif()

find_package(ament_cmake REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(builtin_interfaces REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME} "msg/TexturedMarker.msg"
  "msg/TexturedMarkerArray.msg"
  DEPENDENCIES builtin_interfaces sensor_msgs geometry_msgs)

set(INCLUDE_DIRS ${ament_cmake_INCLUDE_DIRS} ${sensor_msgs_INCLUDE_DIRS}
  ${rosidl_default_generators_INCLUDE_DIRS} ${geometry_msgs_INCLUDE_DIRS})
include_directories(${INCLUDE_DIRS})

set(LIBRARY_DIRS ${ament_cmake_LIBRARY_DIRS} ${sensor_msgs_LIBRARY_DIRS}
  ${rosidl_default_generators_LIBRARY_DIRS} ${geometry_msgs_LIBRARY_DIRS})

link_directories(${LIBRARY_DIRS})

set(LIBS ${ament_cmake_LIBRARIES} ${sensor_msgs_LIBRARIES}
  ${rosidl_default_generators_LIBRARIES} ${geometry_msgs_LIBRARIES})

ament_export_dependencies(ament_cmake)
ament_export_dependencies(sensor_msgs)
ament_export_dependencies(rosidl_default_generators)
ament_export_dependencies(geometry_msgs)
ament_export_include_directories(${INCLUDE_DIRS})

ament_package()
