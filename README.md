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

#### How to create a map:

1. Record data while driving in the environment:

        roslaunch lidar_turtlebot_cartographer record.launch
    
2. Run offline cartographer node (creates .pbstream-file):

        roslaunch lidar_turtlebot_cartographer turtlebot_offline.launch bag_filenames:=/....
    
3. Create map:

        roslaunch lidar_turtlebot_cartographer turtlebot_map_creation.launch bag_filenames:=/...

#### Run multi-map navigation (on the robot):

    roslaunch lidar_turtlebot_bringup indoor_3d.launch
    roslaunch lidar_turtlebot_navigation scan_navigation.launch
    roslaunch multi_map_navigation multi_map_navigation.launch


#### Set goals for navigation and visualize the robot and the laser-scan data (on desktop):

	xhost local:[docker-container-id] (that the container has access to the diplay)
	rviz -d /catkin_ws/src/multi_map_navigation/multi_map_navigation/rviz/multi_map.rviz



[ROS]: http://www.ros.org
[rviz]: http://wiki.ros.org/rviz
[gazebo]: http://gazebosim.org/
[cartographer]: http://wiki.ros.org/cartographer
