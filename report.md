# COSC69.13/269, Spring Term 2021, PA2 - Multi Robot Flocking, Anmol Chachra
My ros package [multi_robot_flocking](https://www.github.com/AnmolChachra/multi_robot_flocking) implements a ros node that demonstrates flocking behavior for
 3 robots in gazebo and 10 robots in stage_ros. Please see the Readme.md for instructions to set up the package. I have also generated a [fork](www.github.com/AnmolChachra/stage_ros) of stage_ros
 that has empty_world.png and empty_world_robots_10.world in its worlds folder that will be used in the launch command. Mult_robot_flocking package simulates the flocking behavior using local behavior, it uses cohesion, separation and alignment to achive this.
 
## Method description
Program is broadly controlled by the following 3 parameters (Note: for now you have to set these values directly in the node file, this will be changed in later releases): 'N' to define the number of robots. Be careful while modifying this parameter, especially when you run for stageros, as you will need to spawn the same number of robots in the world file of stageros and also in the launch file in this package 'stageros.launch'; 'C' to define the cohesion coeffecient - greater the value of 'C', more close robots tends to be, 'S' to define the separation coeffecient - more the separation coeffecient, more the robots try to stay away from each other. Note that you need to find a balance between '
C' and 'S' as increasing one means other's impact is now reduced.

Program starts off by calling a main function that sets up the parameters,instantiate the node and call 'flock' method of 'MultiRobotFlocker' class. During the instantiation process, the node in return sets up the following publisher - 'Twist' to publish the linear velocity and angular velocity. Also, it sets the following subscribers *for each robot* - 'Odometry' to fetch the ground truth position and orientation of the robots as it changes, 'LaserScan' to determine if there is any obstacle that is close to a particular robot.

Program then calls 'flock' method of the instantiated class object that uses the current position and Yaw angle of the robot to calculate the cohesion target position and then updates the target position by applying separation. Once the target is calculated, the slope angle is calculated using tan inverse function and relative angle difference is used to move the robot to the set location. Note that in our simulation the robot constantly moves with a linear velocity set using 'LINEAR_VELOCITY', so the angle is use to steer the motion.

## Evaluation
Program was evaluated for 3 robots in gazebo and 10 robots in stageros. Coeffecient values that works best for 10 robots are 0.2 for cohesion and 4 for separation, whereas for gazebo setting both to 1 seems to work. One can play around with these values to further evaluate the behavior. Please see the video folder provided in the package main directory.
