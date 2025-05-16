cmake_minimum_required(VERSION 3.5)
project(velathrobotics_ros2)

# Add each package as a subdirectory
add_subdirectory(velathrobotics_description)
add_subdirectory(velathrobotics_driver)
add_subdirectory(velathrobotics_gazebo)
add_subdirectory(velathrobotics_input_manager)
