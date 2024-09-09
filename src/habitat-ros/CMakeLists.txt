cmake_minimum_required(VERSION 3.0.2 FATAL_ERROR)

project(habitat_ros
    VERSION 0.1.0
    DESCRIPTION "A ROS interface to Habitat-Sim"
    HOMEPAGE_URL "https://bitbucket.org/smartroboticslab/habitat-ros.git"
    LANGUAGES NONE
)

find_package(catkin REQUIRED COMPONENTS
    geometry_msgs
    nav_msgs
    rospy
    sensor_msgs
    std_msgs
)

catkin_package(
    CATKIN_DEPENDS
        geometry_msgs
        message_runtime
        nav_msgs
        rospy
        sensor_msgs
        std_msgs
)

catkin_install_python(
    PROGRAMS habitat_node.py habitat_mav_sim_node.py
    DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)