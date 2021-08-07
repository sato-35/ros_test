
1. gmapping
	$ roslaunch diff_mobile_robot diff_mobile_gazebo.launch		(window 1)
	$ roslaunch diff_mobile_robot gmapping.launch			(window 2)
	$ cd ~/catkin_ws/src/diff_mobile_robot				(window 3)
	$ chmod +x key_teleop.py					(window ")
	$ cd ~/catkin_ws/						(window ")
	$ rosrun diff_mobile_robot key_teleop.py			(window ")

2.map_saver(question 1)
	$ cd ~/catkin_ws/src/diff_mobile_robot		(window 4)
	$ mkdir map					(window ")
	$ cd map					(window ")
	$ rosrun map_server map_saver -f testmap	(window ")

3.Self-position estimation of mobile robot by AMCL
	($ sudo apt-get install ros-kinetic-amcl)
	( or $ sudo apt-get install ros-melodic-amcl)

	$ roslaunch diff_mobile_robot diff_mobile_gazebo.launch		(window 1)
	$ roslaunch diff_mobile_robot amcl.launch			(window 2)
	$ rviz rviz							(window 3)
