# Drone environment

This package is a testbed for drone algorithm for shore line and object detection.

## dependency
1. MAVROS and MAVLINK
```
sudo apt-get install ros-melodic-mavros ros-melodic-mavros-extras 
ros-melodic-mavlink
```
```
wget https://raw.githubusercontent.com/mavlink/mavros/master/mavros/scripts/install_geographiclib_datasets.sh
sudo bash ./install_geographiclib_datasets.sh 
```

2. Plugins
* jinja
```
sudo apt-get install libprotobuf-dev libprotoc-dev protobuf-compiler libeigen3-dev libxml2-utils python-rospkg python-jinja2
```

* gstreamer
```
sudo apt-get install libgstreamer-plugins-base1.0-dev gstreamer1.0-plugins-bad gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-ugly -y
```

* sitl_gazebo (go to home directory by just typing ``cd``)
```
mkdir -p ~/src
cd src
git clone --recursive https://github.com/PX4/sitl_gazebo.git
cd ~/src/sitl_gazebo
mkdir build
cd build
cmake ..
make -j$(nproc) -l$(nproc)
```

* __export plugin path__
```
export SITL_GAZEBO_PATH=$HOME/src/sitl_gazebo
```

__You can encounter some errors on docker while building it__:
Install the following and rebuild.

* related to jinja2
```
sudo apt-get install python3-pip
sudo pip3 install Jinja2
```
* related to numpy
```
sudo pip3 install numpy
```


## installtion
* clone this (drone_environment) repository into your workspace 
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
        2. winding valley with objects (``use this``: drone, buoy, ASV)
        ```
        roslaunch drone_environment winding_valley.launch background:=BOOL
        ```