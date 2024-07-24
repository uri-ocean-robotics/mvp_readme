# MVP Fraemwork instructions

## Introduction
Marine vehicle packages (MVP) is a ROS-based Guidance and Control framework designed for marine robots. 
MVP works with `robot-localization` to form a Guidance Navigation and Control (GNC) system.
Interfaces are available to simulate vehicles in the `Stonefish` (a OpenGL based simulator).

## Roadmap and support
The MVP framework is under GPL-3.0 license. 
The current releases are tested in ROS-noetic, Ubuntu 20.04, forked Stonefish simulator, and our Stonefish MVP wrapper.
We are migrating to ROS2-Jazzy by the end of 2024.
ROS2 version will be compatible with up-to-date Stonefish simulator, and Stonefish ROS2 wrapper.

## Related repositories.
MVP are managed in a list of repositories as listed below.

### [`mvp_control`](https://github.com/uri-ocean-robotics/mvp_control) 
MVP control is a low-level multi-input-multi-output (MIMO) PID controller which uses thruster allocation and QP solver to compute the "best" thruster commands.
Users could configure different states (position, euler angle, angular and linear vleocity) to be controlled in different frames in the TF-tree.
It leverages the TF packages to transform any set-points into the user-defined frame and child frame before the PID controller.
The thruster allocation matrix is created automatically from TF-trees for different thrusters, maximizing the scalabibility and customizability of the controller.



