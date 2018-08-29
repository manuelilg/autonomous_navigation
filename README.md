# autonomous_navigation

## Overview

Multi-Map Navigation of a autonomous robot with cartographer 

**Keywords:** navigation, multi-map, localization, cartographer


The autonomous_navigation package has been tested under [ROS] Kinetic and Ubuntu 16.04. This is research code, expect that it changes often and any fitness for a particular purpose is disclaimed.

## Installation


### Use Docker-Container

#### Dependencies

- [Docker] (https://www.docker.com/)
Installation https://docs.docker.com/install/linux/docker-ce/ubuntu/ (and not with apt install docker)

The package autonomous_navigation with all dependencies is installed in the Docker-Container
https://hub.docker.com/r/manuelilg/autonomous_navigation/

	docker pull manuelilg/autonomous_navigation
	docker run ... (see Description from Docker-Repository)
	
### Building from Source

#### Dependencies

- [Robot Operating System (ROS)](http://wiki.ros.org) (middleware for robotics),
- [catkin_tools] (https://catkin-tools.readthedocs.io/en/latest/)
- [multi_map_navigation] (https://github.com/manuelilg/multi_map_navigation)
- [lidar_turtlebot] (https://github.com/manuelilg/lidar_turtlebot)

#### Building

To build from source, clone the latest version from this repository into your catkin workspace and compile the package using

	cd catkin_workspace/src
	git clone https://github.com/manuelilg/autonomous_navigation.git
	<install all other dependencies (ros-packages) and sub-dependencies (according to Readme from other packages)>
	cd ../
	rosdep update
	rosdep install --from-paths src --ignore-src -r -y
	catkin build

## Usage

####How to create a map:

1. Record data while driving in the environment:

        roslaunch TODO
    
2. Run offline cartographer node (creates .pbstream-file):

        roslaunch TODO
    
3. Create map:

        roslaunch TODO

####Run multi-map navigation:

    roslaunch TODO


####Set goals for navigation and visualize the robot and the laser-scan data:

	roslaunch TODO


## Launch files

TODO


## Config files

[ROS]: http://www.ros.org
[rviz]: http://wiki.ros.org/rviz
[gazebo]: http://gazebosim.org/
[cartographer]: http://wiki.ros.org/cartographer
[sensor_msgs/Temperature]: http://docs.ros.org/api/sensor_msgs/html/msg/Temperature.html
