# Robotics-Software-Engineering-Nanodegree_MapMyWorld

# Goal
In this project you will create a 2D occupancy grid and 3D octomap from a simulated environment using your own robot with the RTAB-Map package.

# Summary of Tasks
You will develop your own package to interface with the rtabmap_ros package.

You will build upon your localization project to make the necessary changes to interface the robot with RTAB-Map. An example of this is the addition of an RGB-D camera.

You will ensure that all files are in the appropriate places, all links are properly connected, naming is properly setup and topics are correctly mapped. Furthermore you will need to generate the appropriate launch files to launch the robot and map its surrounding environment.

When your robot is launched you will teleop around the room to generate a proper map of the environment.

# Project Requirements
Gazebo >= 7.0  

# Project Setup
Run Update On Linux Command Line:   
```bash
$ sudo apt-get update && sudo apt-get upgrade -y
```  


# Project Directory
 ```bash
 .Project4                                            # Map My World Project  
 ├── my_robot                                          
 │   ├── config                                       # Localization Parameters
 │   │   ├── MACOSX
 │   │   │   ├── ._base_local_planner_params.yaml
 │   │   │   ├── ._costmap_common_params.yaml
 │   │   │   ├── ._global_costmap_params.yaml
 │   │   │   ├── ._local_costmap_params.yaml
 │   │   ├── base_local_planner_params.yaml           # Localization Params for Local Planner
 │   │   ├── config_file.rviz                         
 │   │   ├── costmap_common_params.yaml               # Localization Params for Common Cost Map
 │   │   ├── global_costmap_params.yaml               # Localization Params for Global Cost Map
 │   │   ├── local_costmap_params.yaml                # Localization Params for Local Cost Map
 │   ├── launch      
 │   │   ├── amcl.launch                              # Launches AMCL Node
 │   │   ├── mapping.launch                           # Launches Mapping Node
 │   │   ├── robot_description.launch                 # Launches Robot 
 │   │   ├── world.launch                             # Launches World
 │   ├── maps  
 │   │   ├── map.pgm                                  # Image of Map
 │   │   ├── my_map.yaml                              # Script of Map used by Robot
 │   ├── meshes 
 │   │   ├── hokuyo.dae                               # Sensor used by Robot
 │   ├── urdf   
 │   │   ├── my_robot.gazebo
 │   │   ├── my_robot.xacro
 │   ├── world                                        # Gazebo World containing models    
 │   │   ├── world2
 │   │   │   ├── model.config
 │   │   │   ├── model.sdf
 │   │   ├── my_world.world                           # Smaller world previously used
 │   │   ├── my_world2.world                          # Larger world used in this project
 ├── CMakeLists.txt                                   # Link libraries 
 ├── package.txt
 └──                              
```


# Run Instructions
Create a workspace:    
```bash
$ mkdir -p /home/workspace/catkin_ws/src
$ cd /home/workspace/catkin_ws/src
```   

Copy code from previous project WhereAmI:
```bash
$ git clone https://github.com/dereklau33/Robotics-Software-Engineering-Nanodegree_MapMyWorld.git
```

Build package:  
```bash
$ cd ..
$ source devel/setup.bash
$ catkin_make
```

Launch the world in Gazebo and RViz:
```bash
roslaunch my_robot world.launch
```   

Launch the teleop node:
```bash
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```   

Launch the RTAB-Map mapping node:
```bash
roslaunch my_robot mapping.launch
```   


