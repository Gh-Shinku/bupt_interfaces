cmake_minimum_required(VERSION 3.8)
project(bupt_interfaces)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

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
  "srv/R2TopControl2025.srv"
  "msg/Joystick.msg"
  "srv/Float2Float.srv"
  "msg/Dt35.msg"
  DEPENDENCIES geometry_msgs std_msgs nav_msgs
)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # comment the line when a copyright and license is added to all source files
  set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # comment the line when this package is in a git repo and when
  # a copyright and license is added to all source files
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
