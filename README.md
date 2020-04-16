**Implementation**
==================

Implementation of the system is explained in the following list (bulleted list explains what is all included in that particular element of the numbered list):
	
 1. gazebo_multirobot.launch
 
    - `empty_world.launch` (starts Gazebo with empty_world)       
    - `view_navigation.launch` (starts Rviz)     
    - `multirobot.launch` (explained in the 2nd element below)

 2. multirobot.launch (Launching one_robot.launch with different namespaces multiple times. One might include as many robots as he/she wants as long as the hardware allows)
    - `one_robot.launch` (launches a single robot with a given namespace. Details about what it all includes are given in the 3rd element)

 3. one_robot.launch
    - `kobuki.launch.xml` (describes a kobuki robot and what its pose should be in the world)
    - `tf` (for necessary transforms between /world and robot_namespace/map)
    - `map_server` (loading the map file for a robot)
    - `robot_state_publisher` (publishes the state of the robot to tf with given frequency)
    - `move_base_gazebo.launch` (starts move_base node with given costmap config files)
    - `amcl.launch.xml` (starts amcl node)
    - `laserscan_nodelet_manager` (generating fake laserscan messages)

**Running the System**
=======
Once you have the "multirobot" file in your workspace, open a terminal window and type:

    roslaunch multirobot gazebo_multirobot.launch

This should start Gazebo and Rviz with 2 turtlebots unless you edit launch files.

I added 3 navigation buttons in Rviz to easily assign 2D Nav Goal for up to 3 robots. If you need more robots in the system, you can either check '**multirobot->rviz->navigation.rviz**' to add more buttons **or** simply right click on 2d nav goal and check '**tool properties**'
