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

### Basic 
How to execute the simulation
```
ros2 launch articubot_one launch_sim.launch.py
```

How to execute rviz2 with the saved configuartion
```
rviz2 -d scr/articubot_onr/config/main.rviz
```

### Slam toolbox
'''
ros2 launch slam_toolbox online_async_launch.py slam_params_file:=src/articubot_one/config/mapper_params_online_async.yaml use_sim_time:=true
'''

### ROS navigation2
```
ros2 run nav2_map_server map_server --ros-args -p yaml_filename:=my_map_save.yaml -p use_sim_time:=true
ros2 run nav2_util lifecycle_bringup map_server

ros2 run nav2_amcl amcl --ros-args -p use_sim_time:=true
ros2 run nav2_util lifecycle_bringup amcl

ros2 launch nav2_bringup navigation_launch.py

ros2 launch nav2_bringup localization_launch.py map:=./my_map_save.yaml use_sim_time:=true
ros2 launch nav2_bringup navigation_launch.py map_subscribe_transient_local:=true

```
In rviz2 change the durability policy of the map topic to "Transient Local"

### ROS 2 Control
How to display the control hardware_interfaces:
```
ros2 control list_hardware_interfaces
```

How to display the controllers:
```
ros2 control list_controllers
```