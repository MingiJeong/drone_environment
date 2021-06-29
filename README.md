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
```
gazebo drone_base.world
```

