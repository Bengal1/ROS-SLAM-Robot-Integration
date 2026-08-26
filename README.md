# ROS-SLAM-Robot-Integration

B.Sc. final project in Electrical Engineering at Tel Aviv University, focused on integrating ROS-based SLAM, sensing, and simulation components into a complete mapping workflow for a mobile robot.

The project combines **RTAB-Map** and **Gmapping** for environment mapping and supports both a **real robot configuration** and a **Gazebo-based simulation environment**.

## Project Overview

This project was developed as part of a larger robotic system designed for autonomous operation inside an aircraft cabin.

The main goal of this repository is to provide the robot's **SLAM and simulation environment**, including:

* ROS-based system integration
* 2D and 3D environment mapping
* RGB-D camera integration
* Real robot configuration
* Gazebo simulation
* Integration of RTAB-Map and Gmapping
* Catkin/CMake-based project structure

## My Contribution

My work focused on **integrating and configuring existing robotics components into a complete working system**, rather than implementing SLAM algorithms from scratch.

The project included:

* Integrating multiple ROS packages into a unified workspace
* Configuring RTAB-Map for RGB-D SLAM and 3D mapping
* Integrating Gmapping for improved 2D occupancy-grid mapping
* Configuring RGB-D and IMU input from an Intel RealSense camera
* Building and configuring the robot simulation environment
* Creating and maintaining ROS launch configurations
* Managing package dependencies and the catkin/CMake build workflow
* Testing the combined mapping system in both simulation and real environments

## System Architecture

The repository contains two main components:

### `hygie` — Real Robot

Contains the ROS configuration for running the SLAM system on the physical robot.

The setup was designed around:

* NVIDIA Jetson Xavier NX or equivalent single-board computer
* Intel RealSense D435i or equivalent RGB-D camera with IMU
* ROS
* RTAB-Map
* Gmapping

### `purebot` — Simulation
<img align="right" width="300" alt="rob1" src="https://github.com/user-attachments/assets/55a0899b-3052-4575-8ffa-5e4a0cb6e454" />
Contains the Gazebo-based robot simulation environment.

The simulation reproduces an aircraft-cabin environment and allows the SLAM configuration to be tested without requiring the physical robot.

## SLAM Approach

The project combines **RTAB-Map** and **Gmapping**.

RTAB-Map provides RGB-D SLAM and 3D mapping capabilities. During development, its standalone 2D occupancy map was found to be relatively noisy for navigation purposes.

Gmapping was therefore integrated alongside RTAB-Map to generate a cleaner 2D occupancy map while retaining RTAB-Map's 3D mapping capabilities.

## RTAB-Map vs. RTAB-Map + Gmapping

Testing was performed in both simulated and real environments.

The combined configuration produced improved 2D maps compared with RTAB-Map alone, while preserving the 3D mapping capabilities provided by RTAB-Map.

### Simulation Mapping

<img width="616" height="416" alt="sim_comp" src="https://github.com/user-attachments/assets/998233fa-75f4-4460-8a2f-819880d6ab45" />


### Real Environment Mapping

<img width="621" height="289" alt="real_comp" src="https://github.com/user-attachments/assets/a0db85f3-39c8-4cdf-8491-cb9f41581176" />


## Technologies

* ROS
* CMake / catkin
* RTAB-Map
* Gmapping
* Gazebo
* Intel RealSense
* RGB-D sensing
* SLAM
* Linux

## Requirements

### Hardware for Real-Robot Operation

* NVIDIA Jetson Xavier NX or equivalent SBC
* Intel RealSense D435i or equivalent RGB-D camera with IMU
* Compatible mobile robot platform

Simulation does not require the physical robot hardware.

## Installation

The project was developed using **ROS Melodic**.

### 1. Install ROS

Install ROS Melodic using the official ROS installation instructions.

### 2. Install ROS Navigation

```bash
sudo apt-get install ros-melodic-navigation
```

### 3. Install Intel RealSense ROS Support

Install the Intel RealSense SDK and ROS integration appropriate for your platform.

For NVIDIA Jetson systems, use the corresponding RealSense installation procedure.

### 4. Install RTAB-Map

```bash
sudo apt install ros-melodic-rtabmap-ros
```

### 5. Install Gmapping

```bash
sudo apt-get install ros-melodic-gmapping
```

### 6. Install Additional Dependencies

```bash
sudo apt-get install ros-melodic-navigation
sudo apt-get install python-opencv
sudo apt-get install python-numpy
sudo apt-get install python-scikits-learn
```

Install the ROS depth-image-to-laser-scan package if required by the selected configuration.

### 7. Clone and Build

Clone the repository into your catkin workspace:

```bash
cd ~/catkin_ws/src/
git clone https://github.com/Bengal1/ROS-SLAM-Robot-Integration.git
cd ..
catkin_make
```

Then source the workspace:

```bash
source devel/setup.bash
```

## Running the Project

### Simulation

```bash
roslaunch purebot purebot_sim.launch
```

### Real Robot

```bash
roslaunch hygie hygie.launch
```

## Project Context

The project was originally developed as part of a larger autonomous robotic platform intended to operate inside aircraft cabins.

This repository focuses specifically on the **robotics integration, SLAM, sensing, and simulation components** required to support environment mapping and localization.

## Results

The main engineering result was the successful integration of several independent robotics components into a unified ROS workflow capable of operating in both simulation and real-world environments.

Combining RTAB-Map with Gmapping improved the quality of the 2D occupancy map used for navigation while retaining RTAB-Map's 3D mapping capabilities.

## Project Videos

Videos demonstrating the project are available through the [project's YouTube channel](https://www.youtube.com/channel/UCwc1qD5aTrj4iaxQrpZu07w).

## Related Work
The project was informed by research in: Simultaneous Localization and Mapping, Grid-based SLAM, Nonlinear state estimation, Robot navigation and collision avoidance.

Related Publications:

[1] Guillaume Bresson, Zayed Alsayed, Li Yu, Sébastien Glaser. Simultaneous Localization and Mapping: A Survey of Current Trends in Autonomous Driving. IEEE Transactions on Intelligent Vehicles,Institute of Electrical and Electronics Engineers, 2017, XX, pp.1. 10.1109/TIV.2017.2749181. hal-01615897.

[2] Giorgio Grisetti, Cyrill Stachniss, Wolfram Burgard, "Improving Grid-based SLAM with Rao-Blackwellized Particle Filters by Adaptive Proposals and Selective Resampling".

[3] Eric A. Wan and Rudolph van der Merwe, " The Unscented Kalman Filter for Nonlinear Estimation", Oregon Graduate Institute of Science & Technology 20000 NW Walker Rd, Beaverton, Oregon 97006.

[4] Dieter Foxy Wolfram Burgardy Sebastian Thrun, "The Dynamic Window Approach to Collision Avoidance", Dept. of Computer Science III, University of Bonn, D-53117 Bonn, Germany, Dept. of Computer Science, Carnegie Mellon University, Pittsburgh, P A 15213

## Repository Structure

```text
.
├── hygie/      # Real robot SLAM configuration
├── purebot/    # Gazebo robot simulation
└── README.md
```

## Author

**Or Ben-Gal**
B.Sc. Electrical Engineering, Tel Aviv University



# AI-for-Robot
This is the final project of my B.sc in Elecrical engineering at [Tel-Aviv University](https://english.tau.ac.il/).
This project is part of a large project - Robot that purify airplane's cabin from viruses.
The project is Implemented with [ROS](https://www.ros.org/) and have some improvement to be done.


This package contains to the robot SLAM application and also the robot simulation.
#### Hygie - Real Robot SLAM
After installing if you will choose to udse thr real SLAM application, it's all in the Hygie folder.
**Hardware requierments:
1. single-board computers (SBC) - Nvidia Jetson Xavier NX or equivalent SBC.
2. RGB-D Camera with IMU - Intel RealSense D435i or equivalent combination. 
3. Robot for implementation (optional).
#### Purebot - Robot Ready Simulation
The purebot folder contains all the necessaries for simulating our robot.

![pbot](https://user-images.githubusercontent.com/34989887/138612685-0de1a7f8-7b38-4606-a113-9617c80e39a2.png)
![pbot5](https://user-images.githubusercontent.com/34989887/138612684-d444c91d-0be5-4604-979c-764922b9471d.png)
![pbot3](https://user-images.githubusercontent.com/34989887/138612682-eb2202cd-2593-4f0e-9902-42c3b00729ec.png)



## Related Publications:
[1] Guillaume Bresson, Zayed Alsayed, Li Yu, Sébastien Glaser. Simultaneous Localization and Mapping: A Survey of Current Trends in Autonomous Driving. IEEE Transactions on Intelligent Vehicles,Institute of Electrical and Electronics Engineers, 2017, XX, pp.1. 10.1109/TIV.2017.2749181. hal-01615897.

[2] Giorgio Grisetti, Cyrill Stachniss, Wolfram Burgard, "Improving Grid-based SLAM with Rao-Blackwellized Particle Filters by Adaptive Proposals and Selective Resampling".

[3] Eric A. Wan and Rudolph van der Merwe, " The Unscented Kalman Filter for Nonlinear Estimation", Oregon Graduate Institute of Science & Technology 20000 NW Walker Rd, Beaverton, Oregon 97006.

[4] Dieter Foxy Wolfram Burgardy Sebastian Thrun, "The Dynamic Window Approach to Collision Avoidance", Dept. of Computer Science III, University of Bonn, D-53117 Bonn, Germany, Dept. of Computer Science, Carnegie Mellon University, Pittsburgh, P A 15213

## Installation Instructions
1. Install ROS - [ROS Installation Instructions](http://wiki.ros.org/melodic/Installation/Ubuntu)
2. Install ROS Navigation Package.
```shell
sudo apt-get install ros-melodic-navigation
```
  For more information go to [ROS-Navigation](http://wiki.ros.org/navigation)

3. Install Realsense Library for ROS.
  
  * Installation of Intel realsense on Nvidia Jetson: [Jetson Installation Guide](https://github.com/IntelRealSense/librealsense/blob/master/doc/installation_jetson.md)
  
  For more information go to [RealSense](https://github.com/mahammadirfan/SLAM-using-intelrealsense-d435i)

4. Install RTAB-Map:
```shell
sudo apt install ros-melodic-rtabmap-ros
```
  For more information go to: [RTAB-Map-ROS](https://github.com/introlab/rtabmap_ros) 

5. Install ROS's Gmapping Package:
```shell
sudo apt-get install ros-melodic-gmapping
sudo apt-get install ros-melodic-navigation
sudo apt-get install python-opencv
sudo apt-get install python-numpy
sudo apt-get install python-scikits-learn
```
  For more Information go to [SLAM Gmapping](http://wiki.ros.org/slam_gmapping)

6. Install [Depth image to Laser scan converter](http://wiki.ros.org/depthimage_to_laserscan)

7. Clone this repository:
```shell
cd ~/catkin_ws/src/
git clone https://github.com/Bengal1/AI-for-Robot.git
cd ..
catkin_make
```

* (Optional) [RRT_Exploration](https://github.com/hasauino/rrt_exploration) Package.

## Activation
Purebot:
```shell
Roslaunch purbot purebot_sim.launch
```
Hygie:
```shell
Roslaunch hygie hygie.launch
```

## The Project:
#### Motivation/Objectives:
The coronavirus pandemic, is an ongoing global pandemic of coronavirus disease 2019 (COVID-19) caused by severe acute respiratory syndrome coronavirus 2 (SARS-CoV-2). The novel virus was first identified in Wuhan, China, in December 2019, and it spread to other parts of mainland China and around the world. The World Health Organization (WHO) declared a Public Health Emergency of International Concern on 30 January 2020, and a pandemic on 11 March 2020. As of 3 October 2021, more than 234 million cases and 4.8 million deaths have been confirmed, making it one of the deadliest pandemics in history.
The motivation for the project stems from the health and economic need to rehabilitate the aviation industry that has experienced huge losses in the last two years, as well as reducing the mobility of the virus. These things that affect the public health and world economy.

The Gazebo environment that we build for the simulation, simulate an airplane's cabin.

![world3](https://user-images.githubusercontent.com/34989887/138612908-41e74862-426e-4231-b60b-603d18b844e1.png)

This project Implements RTAB-Map as well as Gmapping. I have found it to improve 2D mapping. the 2D mappinimg of RTAB-Map only is quite noisy and It make it difficult for the robot to navigate in the environment.
### RTAB-Map vs RTAB-Map+Gmapping
We have found that combining RTAB-Map and Gmapping provides better 2D map then only RTAB-Map and do not eopardise the 3D mapping of the RTAB-Map which it excel at.
You may see the differance on the Real environment mapping and on simulation mapping:
#### Simulation Mapping:
![image](https://user-images.githubusercontent.com/34989887/138611701-9e079077-a8c5-4db5-8d57-673bbdc8acb0.png)

#### Real Environment Mapping:
![image](https://user-images.githubusercontent.com/34989887/138611711-fffd7097-48a7-4b45-b6d0-e486dc7aee8a.png)


For videos of of the project go to [Poject YouTube Channel](https://www.youtube.com/channel/UCwc1qD5aTrj4iaxQrpZu07w).
