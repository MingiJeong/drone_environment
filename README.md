# Drone environment

This package is a testbed for drone algorithm for shore line and object detection.

## installtion
* clone this repository into your workspace 
* run `catkin_make` in your workspace
* export gazebo model path as per the following command
```
export GAZEBO_MODEL_PATH=$GAZEBO_MODEL_PATH:<path to your model>
```

## run
* In a terminal (in the package's world directory), type the following command:
    - On Gazebo without ROS
        1. drone base world
        ```
        gazebo drone_base.world
        ```
        2. winding valley with objects
        ```
        gazebo base_winding_valley.world
        ```
    - ROS environment
        - Argument
            - background: true (load terrain, default) / false (only water)
        
        1. drone base world
        ```
        roslaunch drone_environment drone_base.launch background:=BOOL
        ```
        2. winding valley with objects
        ```
        roslaunch drone_environment winding_valley.launch background:=BOOL
        ```