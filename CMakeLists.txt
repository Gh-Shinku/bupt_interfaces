cmake_minimum_required(VERSION 3.8)
project(bupt_interfaces)

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(std_msgs REQUIRED)
find_package(nav_msgs REQUIRED)

# 声明srv等文件所属的工程名字, 文件位置, 依赖DEPENDENCIES
find_package(rosidl_default_generators REQUIRED)
rosidl_generate_interfaces(${PROJECT_NAME}
  "srv/R1TopControl.srv"
  "srv/ControlState.srv"
  "srv/JoyStickInteraction.srv"
  "srv/FineAdjust.srv"
  "srv/OdomCorrect.srv"
  "srv/AnalyseTrajetory.srv"
  "srv/ShootParams.srv"
  "srv/GetAveOdom.srv"
  "srv/ActionControl.srv"
  "srv/ActionInfo.srv"
  "srv/CalculateRpm.srv"
  "msg/Joystick.msg"
  "msg/Dt35.msg"
  DEPENDENCIES geometry_msgs std_msgs nav_msgs
)

ament_package()
