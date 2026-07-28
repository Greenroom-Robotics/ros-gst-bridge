cmake_minimum_required(VERSION 3.5)
project(audio_msgs)

# Default to C99
if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(std_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)

set(msg_files
  "msg/Audio.msg"
)

## Generate added messages and services with any dependencies listed here
rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  DEPENDENCIES builtin_interfaces std_msgs
)





if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # Skip the ROS style linters. This code is inherited from upstream
  # ros-gst-bridge and does not follow them; reformatting to comply would churn
  # every file and conflict with future upstream merges without saying anything
  # about whether the code works. cppcheck and pep257 still run.
  set(AMENT_LINT_AUTO_EXCLUDE
    ament_cmake_copyright
    ament_cmake_cpplint
    ament_cmake_uncrustify
    ament_cmake_flake8
    ament_cmake_lint_cmake
    ament_cmake_xmllint
  )
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
