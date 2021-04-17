# multi_robot_flocking
Simulate flocking behavior through local behaviors for multiple robots

## Requirements
<ul><li>ROS -- tested on Melodic, but other versions may work
  </li><li>catkin_make -- used for building the application</li><li>stage_ros -- https://github.com/AnmolChachra/stage_ros (clone this in your src dir)</li><li>turtlebot3_description -- https://github.com/AnmolChachra/turtlebot3_description (clone this in your src dir)</li></ul>

## Build
Once cloned in a ROS workspace, e.g. `/root/catkin/`, run the following commands to build it:
```
catkin_make
```
## Run
### Run for gazebo
```
roslaunch multi_robot_flocking gazebo.launch
```
### Run for stageros
```
roslaunch multi_robot_flocking stageros.launch
```

## Note
By default N in multi_robot_flocking/src/multi_robot_flocking is set to 3. When running for stageros, set this value to 10
  
