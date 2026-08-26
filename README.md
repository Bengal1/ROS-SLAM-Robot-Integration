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

Contains the Gazebo-based robot simulation environment.

The simulation reproduces an aircraft-cabin environment and allows the SLAM configuration to be tested without requiring the physical robot.

<img align="left" height="230" alt="rob3" src="https://github.com/user-attachments/assets/505a1597-2036-4dcd-bbd3-b9e4cd0a2830" /><img align="center" height="230" alt="rob2" src="https://github.com/user-attachments/assets/1d3ace90-d9d9-4440-8a08-a9042712fec0" /><img align="right" height="230" alt="rob1" src="https://github.com/user-attachments/assets/55a0899b-3052-4575-8ffa-5e4a0cb6e454" /> 
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
