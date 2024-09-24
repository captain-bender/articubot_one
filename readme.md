# articubot_one (modified)

This is a modified version of the articubot_one as presented by the [articulated robotics](https://articulatedrobotics.xyz/) blog.

The working version is based on ROS 2 Humble and Gazebo Classic 11. The majority of the changes is based on turtlebot3 official Robotis repository.

## ROS 2 Control

Required packages:
```
sudo apt install ros-humble-ros2-control
sudo apt install ros-humble-ros2-controllers
sudo apt install ros-humble-gazebo-ros2-control
```

## Frequently used commands
How to execute the simulation
```
ros2 launch articubot_one launch_sim.launch.py
```

How to execute rviz2 with the saved configuartion
```
rviz2 -d scr/articubot_onr/config/main.rviz
```

How to display the control hardware_interfaces:
```
ros2 control list_hardware_interfaces
```

How to display the controllers:
```
ros2 control list_controllers
```