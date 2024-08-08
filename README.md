# Launch TurtleBot Navigation

This guide provides detailed steps to install the TurtleBot packages, set up a simulation environment, create a map, and launch navigation for TurtleBot.

## Prerequisites

Ensure you have the following installed:
- Ubuntu 20.04
- ROS Noetic

## Installation Steps

### 1. Install TurtleBot Packages

Open a terminal and execute the following commands to install TurtleBot packages:

```bash
sudo apt-get update
sudo apt-get install ros-noetic-turtlebot3
```

### 2. Install TurtleBot Simulation Packages

Next, install the simulation packages for TurtleBot:

```bash
sudo apt-get install ros-noetic-turtlebot3-simulations
```

![1](https://github.com/user-attachments/assets/0c20a762-fe8b-417d-8471-b7e64b0a8e2d)

### 3. Set Up Environment Variables
Add the TurtleBot model to your environment variables. Append the following lines to your ~/.bashrc file:\

```bash
echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc
source ~/.bashrc
```

![2](https://github.com/user-attachments/assets/d56f6330-64f8-4193-882a-01077fb0e5ee)


### 4. Create a Map and Launch Navigation
4.1 Launch the TurtleBot World
Start by launching the TurtleBot world in Gazebo:

```bash
roslaunch turtlebot3_gazebo turtlebot3_world.launch
```
![3](https://github.com/user-attachments/assets/b56b8edb-1277-4fde-a1eb-f1e1c0c79a91)

4.2 Launch SLAM for Mapping
To create a map using SLAM (Simultaneous Localization and Mapping), run:

```bash
roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
```
![4](https://github.com/user-attachments/assets/ccc15ed0-b979-463e-8b2e-2bfe1f803465)

You can save the map by running:

```bash
rosrun map_server map_saver -f ~/map
```

4.3 Launch Navigation
Finally, launch the navigation stack:

```bash
roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml
```
![5](https://github.com/user-attachments/assets/d6e5cf8b-6895-45c9-ad5e-4c05b604d235)


## Additional Dependencies
Ensure all dependencies are installed. If not, you can install them using the following commands:

```bash
sudo apt-get install ros-noetic-navigation
sudo apt-get install ros-noetic-slam-gmapping
```

 
## Troubleshooting
- If you encounter issues with missing dependencies, use rosdep to install them:

```bash
sudo rosdep init
rosdep update
rosdep install --from-paths src --ignore-src -r -y
```
![7](https://github.com/user-attachments/assets/4ddca7e0-d398-4b6a-8a2c-58833feecc34)
![6](https://github.com/user-attachments/assets/eea01d10-e886-4a44-b191-77576f510cc3)

- Ensure all necessary environment variables are correctly set by sourcing your .'bashrc':

```bash
source ~/.bashrc
```

## References
ROS Wiki
TurtleBot3


This guide should help you set up and navigate your TurtleBot. If you have any issues, refer to the ROS Wiki or the TurtleBot3 e-Manual.






