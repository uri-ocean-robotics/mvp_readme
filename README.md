# MVP Framework instructions (ROS-noetic)

## Introduction
Marine vehicle packages (MVP) is a ROS-based Guidance and Control framework designed for marine robots. 
MVP works with `robot-localization` to form a Guidance Navigation and Control (GNC) system.
Interfaces are available to simulate vehicles in the `Stonefish` (a OpenGL based simulator).

## Roadmap and support
The MVP framework is under GPL-3.0 license. 
The current releases are tested in ROS-noetic, Ubuntu 20.04, forked Stonefish simulator, and our Stonefish MVP wrapper.
We are migrating to ROS2-Jazzy by the end of 2024.
ROS2 version will be compatible with up-to-date Stonefish simulator, and Stonefish ROS2 wrapper.
The MVP framework will be actively maintained at least in the next 5 years with the support from NSF grants.

## Brief information about related repositories.
MVP are managed in a list of repositories as listed below.

### [mvp_control](https://github.com/uri-ocean-robotics/mvp_control) 
MVP control is a low-level multi-input-multi-output (MIMO) PID controller which uses thruster allocation and QP solver to compute the "best" thruster commands.
Users could configure different states (position, euler angle, angular and linear vleocity) to be controlled in different frames in the TF-tree.
It leverages the TF packages to transform any set-points into the user-defined frame and child frame before the PID controller.
The thruster allocation matrix is created automatically from TF-trees for different thrusters, maximizing the scalabibility and customizability of the controller.

### [mvp_mission](https://github.com/uri-ocean-robotics/mvp_mission)
MVP mission is the guidance system which commands desired set points for vehicle poses based on higher-level behaviors, such as path following and teleoperation.
The core of MVP mission uses a user-configurable ***finite-state machine*** where multiple behaviors can be attached to a state with different priority-levels. 
The setpoint (output from mvp mission helm) will be determined based on the active behaviors for each degree-of-freedom. ***For example***, in path-3D state, if periodical-surfacing behavior is actively sending desired depth with a higher priority than the path-following behavior, the set-point of vehicle depth will be from the periodical surfacing but heading, pitch and surge set point will still from the path-following behavior.

### [mvp_msgs](https://github.com/uri-ocean-robotics/mvp_msgs)
MVP msgs contains all the customized ROS messages and services for MVP framework.

### [mvp_utilites](https://github.com/uri-ocean-robotics/mvp_utilities)
MVP utilies contains a list of nodes for sensor processing either in the virtual environment or on the real vehicle. ***For example***, there are tools for imu calibration and filtering, and nodes for publishing the TF between world and odom based on GPS fix and local odometry.

### [mvp_hardware_drivers](https://github.com/uri-ocean-robotics/mvp_hardware_drivers)
This repository contains ros nodes and external modules for running real sensors, such as IMU, DVL, and pressure sensors.

### [mvp_gui](https://github.com/uri-ocean-robotics/mvp_gui)
This is a GUI program for easy operation. It has a map page for publishing new waypoints and monitoring vehicle status.
In real operation, this GUI program will run on a computer with ROS MASTER exported to the AUV's IP address.
And every person in the same network can access the GUI through a web link.

### [world_of_stonefish](https://github.com/uri-ocean-robotics/world_of_stonefish)
This repository contains configuration and drivers (ROS2 only) for interfacing with Stonefish ROS wrapper.

### [stonefish_mvp](https://github.com/uri-ocean-robotics/stonefish_mvp)
This is a ROS wrapper for stonefish simulator. This repository is depreciated in our MVP framework in ROS2-jazzy, and we will directly use the official `stonefish_ros2` wrapper.

### [stonefish](https://github.com/uri-ocean-robotics/stonefish)
This is a forked repo of the official stonefish simulator. We are mainly testing the MVP framework with this version of the Stonefish.
The ROS1 version of the MVP will not be compatible most up-to-date stonefish, due to the lack of updates in the Stonefish MVP wrapper.
ROS2 version of the MVP will be compatible with the up-to-date stonefish.


## Installation instruction
We have multiple AUVs running MVP framework, the most up-to-date instruction can be found under [alpha_rise_auv](https://github.com/GSO-soslab/alpha_rise_auv) where you can find instructions for running a simulation environment.


## AUV Hardware resources.
The mechanical and electronics design of the AUV ALPHA can be found under our [hardware release repository](https://github.com/GSO-soslab/alpha_hardware_release)

