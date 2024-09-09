ExplORB-SLAM
============

A package for Active visual SLAM using the structure of the underlying pose-graph.

Code used for the paper "ExplORB-SLAM: Active Visual SLAM Exploiting the Pose-graph Topology", accepted for presentation in the Fifth Iberian Robotics Conference (ROBOT 2022).

Tested by jplaced for Ubuntu 20.04, ROS Noetic.

Contact: jplaced@unizar.es, jjgomez@unizar.es

Citation
------------

Placed, J. A., Gómez-Rodríguez, J. J., Tardós, J. D., & Castellanos, J. A. (2022). ExplORB-SLAM: Active Visual SLAM Exploiting the Pose-graph Topology. In 2022 Fifth Iberian Robotics Conference (ROBOT).

Detected dependencies:
------------
- Eigen
- OpenCV
- Python3
  * Numpy
  * Sklearn
  * Numba
  * OpenCV
- Gazebo
- ROS Noetic
  * rviz
  * turtlebot3_teleop
  * gazebo_ros
  * octomap_ros
  * octomap_rviz_plugins
  * move_base

Building
------------
1. Clone repo:
```bash
git clone https://github.com/JulioPlaced/ExplORBSLAM.git

# install dependency
sudo apt install -y ros-noetic-turtlebot3-teleop \
          ros-noetic-move-base \
         ros-noetic-octomap-rviz-plugins \
         ros-noetic-kobuki-msgs \
         ros-noetic-octomap \
         ros-noetic-octomap-ros \
         ros-noetic-teb-local-planner 
```

Build the habitat simulator using python>=3.9

2. Build repo:
```bash
cd ExplORBSLAM/
catkin build
```

3. Remember to source the ExplORBSLAM workspace:

```bash
source devel/setup.bash
```

If sourcing doesn't work properly, try

```bash
catkin config --no-install
catkin clean --all
```

and rebuild.

Issues
------------

Some issues with using habitat. One problem is the `libffi.7.so` library for python>=3.9 (under `miniconda3/env/habitat/lib`) will point to `libffi.so.8`. This will cause issue.

The solution is to point it back to version 7, using the library in `/lib/x86_64-linux-gnu/libffi.so.7.1.0.` The directory looks like this:

```plaintext
libffi.7.so -> /lib/x86_64-linux-gnu/libffi.so.7.1.0
libffi.8.so -> libffi.so.8.1.2
libffi.a
libffi.so -> /lib/x86_64-linux-gnu/libffi.so.7.1.0
libffi.so.7 -> /lib/x86_64-linux-gnu/libffi.so.7.1.0
libffi.so.8 -> libffi.so.8.1.2
libffi.so.8.1.2
````



Running
------------
1. Launch the scenario:

AWS house environment:
```bash
roslaunch robot_description single_house.launch
```
Or AWS bookstore environment:
```bash
roslaunch robot_description single_bookstore.launch
```
Or Habitat Simulator 
```bash
roslaunch robot_description single_habitat.launch
```

2. Launch the decision maker
```bash
roslaunch decision_maker autonomous_agent.launch
```
