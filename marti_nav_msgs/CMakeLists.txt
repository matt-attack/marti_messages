cmake_minimum_required(VERSION 3.5)
project(marti_nav_msgs)

# Add support for C++11
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 11)
endif()

find_package(ament_cmake REQUIRED)
find_package(std_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(marti_common_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(builtin_interfaces REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME} 
  "msg/Command.msg" 
  "msg/GridMap.msg"
  "msg/LeadVehicle.msg" 
  "msg/Obstacle.msg" 
  "msg/ObstacleArray.msg"
  "msg/PathPlanning.msg" 
  "msg/Route.msg" 
  "msg/RouteOffset.msg"
  "msg/RoutePoint.msg" 
  "msg/RoutePosition.msg" 
  "msg/RouteSpeed.msg"
  "msg/RouteSpeedArray.msg" 
  "msg/TeleopState.msg" 
  "msg/TrackedObject.msg"
  "msg/TrackedObjectArray.msg" 
  "msg/VehicleControl.msg" 
  "msg/Wgs84Sample.msg"
  "srv/DeleteRoute.srv" 
  "srv/GetRoute.srv" 
  "srv/GetRouteList.srv"
  "srv/PlanRoute.srv" 
  "srv/SaveRecordedRoute.srv" 
  "srv/SaveRoute.srv"
  "srv/SetRoute.srv" 
  "srv/UpdateRouteMetadata.srv"
  DEPENDENCIES 
  builtin_interfaces
  std_msgs
  geometry_msgs
  sensor_msgs
  marti_common_msgs
)

set(INCLUDE_DIRS ${${BUILD_DEPS}_INCLUDE_DIRS} ${ament_cmake_INCLUDE_DIRS})
include_directories(${INCLUDE_DIRS})

set(LIBRARY_DIRS ${${BUILD_DEPS}_LIBRARY_DIRS} ${ament_cmake_LIBRARY_DIRS})

link_directories(${LIBRARY_DIRS})

set(LIBS ${${BUILD_DEPS}_LIBRARIES} ${ament_cmake_LIBRARIES})

set(MSG_DEPS 
  #geographic_msgs 
  geometry_msgs marti_common_msgs sensor_msgs
  std_msgs)

set(BUILD_DEPS ${MSG_DEPS})

set(RUNTIME_DEPS ${MSG_DEPS})

ament_export_dependencies(${BUILD_DEPS})
ament_export_dependencies(ament_cmake)
ament_export_include_directories(${INCLUDE_DIRS})

ament_package()
