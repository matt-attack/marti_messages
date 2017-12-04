cmake_minimum_required(VERSION 3.5)
project(marti_common_msgs)

# Add support for C++11
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 11)
endif()

find_package(rosidl_default_generators REQUIRED)
find_package(ament_cmake REQUIRED)
find_package(std_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(builtin_interfaces REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME} "msg/BoolStamped.msg"
  "msg/ByteArrayStamped.msg" "msg/DurationStamped.msg" "msg/Float32Stamped.msg"
  "msg/Float64Stamped.msg" "msg/HealthStatus.msg" "msg/Int16Stamped.msg"
  "msg/Int32Stamped.msg" "msg/Int64Stamped.msg" "msg/Int8Stamped.msg"
  "msg/KeyValue.msg" "msg/KeyValueArray.msg" "msg/StringArrayStamped.msg"
  "msg/StringStamped.msg" "msg/TimeStamped.msg" "msg/UInt16Stamped.msg"
  "msg/UInt32Stamped.msg" 
  "msg/UInt64Stamped.msg" 
  "msg/UInt8Stamped.msg"
  DEPENDENCIES builtin_interfaces std_msgs)

get_cmake_property(_variableNames VARIABLES)
foreach (_variableName ${_variableNames})
    message(STATUS "${_variableName}=${${_variableName}}")
endforeach()

set(INCLUDE_DIRS ${rosidl_default_generators_INCLUDE_DIRS}
  ${ament_cmake_INCLUDE_DIRS} ${std_msgs_INCLUDE_DIRS})
include_directories(${INCLUDE_DIRS})

set(LIBRARY_DIRS ${rosidl_default_generators_LIBRARY_DIRS}
  ${ament_cmake_LIBRARY_DIRS} ${std_msgs_LIBRARY_DIRS})

link_directories(${LIBRARY_DIRS})

set(LIBS ${rosidl_default_generators_LIBRARIES} ${ament_cmake_LIBRARIES}
  ${std_msgs_LIBRARIES})

ament_export_dependencies(rosidl_default_generators)
ament_export_dependencies(ament_cmake)
ament_export_dependencies(std_msgs)
ament_export_include_directories(${INCLUDE_DIRS})

ament_package()
