## Tips
- catkin_make is a command line tool which adds some convenience to the standard catkin workflow. You can imagine that catkin_make combines the calls to cmake and make in the standard CMake workflow.
- if you don't have a launch file, you can use rosrun instead of roslaunch to run your code. 
- Whenever changing a c++ file, always run catkin_make becz of the compiler
- CMakeLists are used by Catkin_make to build all of the packages in ros 
- Run catkin_make whenever a .cc or .cpp is changed, but not necessarily the case for .launch files
- ROS_INFO_STREAM: command to print into the /rosout topic in ROS
- Whenever using a new package, always check the configuration files at the beginnning bcz it's sensitive to the config files.
As a sequence:
a) first double check Ids-parameters in Launch File
b) Yaml File
c) source File -- double check for hard coded names
root cause the problem then work towards a solution 

## Commands
1) catkin_make:
```
catkin_make --pkg orb_slam2_ros: only build this package
```

2) rqt - graph visualizations:
```
rqt_graph:
rqt_plot:
rqt_image_view: plotting topics streamed from the camera, kind of like rviz in a sense
rosrun rqt_reconfigure rqt_reconfigure: command to change both static/dynamic parameters
```

3) rostopic:
```
$ ros topic list | grep slam
$ rostopic echo /rosout | grep SLAM: we can use the rosout topic for debugging, by going into the source code
and using the print command ROS_INFO_STREAM("SLAM: No Points!!");
$ rostopic info /topic_name: publishers/subscribers
$ rostopic hz     # display publishing rate of topic
```

## Building a package
- The simplest possible package might have a structure which looks like this:
``` 
my_package/
  CMakeLists.txt
  package.xml

$ catkin_create_pkg <package_name> [depend1] [depend2] [depend3]
$ catkin_create_pkg beginner_tutorials std_msgs rospy roscpp
```

`ros::init(argc, argv, "talker");` : initialize ROS. This allows ROS to do name remappiong through the command line -- not importnat for now. 
This is also where we specify the name of our node. Node names must be unique in a running system.

`ros::NodeHandle n;` : Create a handle to this process node. The first NodeHandle created will actually do the initialization of the node, and
the last one destructed will cleanup any resources the node was using.

`ros::Subscriber subDepth = n.subscribe("/zed2/zed_node/depth/depth_registered", 10, depthCallback);`

`ros::Publisher myPublisher = n.advertise<std_msgs::String>("hussein",1000);`

`ros::Publisher chatter_pub = n.advertise<std_msgs::String>("chatter", 1000);` : Tell the master that we are going to be publishing a message of type 
std_msgs/String on the topic chatter.

`ros::Rate loop_rate(10);` : a ros::Rate object allows you to specify a freq that you would like to loop at. It will keep track of how long it has been
since the last call to Rate::sleep(), and sleep for the correct amount of time.

`while (ros::ok());` : once ros::ok() returns false, all ROS calls will fail. 

`std_msgs::String msg;`

`ROS_INFO("%s", msg.data.c_str());` : ROS_INFO is a replacement for printf/cout.

`ROS_INFO("Looping");`

`ros::spinOnce();` : used when receiving any callbacks. Whenever you add a subscription into an application, and don't have ros::spinOnce() your callbacks would never get called.

`loop_rate.sleep();`


## Libraires used:

`#include "ros/ros.h"` : is a convenience include that includes all the headers necessary to use the most common public
pieces of the ROS system

`#include "std_msgs/String.h"` : this includes the std_msgs/String message, which resides in the std_msgs package. This is a header
generated automatically from the String.msg file in that package. The second arguement is the size of our publishing queue.
In this case if we are publishing too quickly it will buffer up a maximum of 1000 messages before beginning to throw away old ones.


## ROS Package has the following structure
- Config
- Include (.h)
- Launch (.launch)
- Src (.cc)

## Cmd_Vel:
- ROS topic that's used to control speeds of robots
- Has a message type geometry_msgs/Twist of the following structure:
`geometry_msgs/Vector3 linear`
`geometry_msgs/Vector3 angular`

## Command to move robot using move base:
```
rostopic pub /move_base_simple/goal geometry_msgs/PoseStamped '{header: {stamp: now, frame_id: "map"}, pose: {position: {x: 1.0, y: 0.0, z: 0.0}, orientation: {w: 1.0}}}'
rostopic pub /move_base_simple/goal geometry_msgs/PoseStamped '{header: {stamp: now, frame_id: "map"}, pose: {position: {x: 1.0, y: 1.0, z: 0.0}, orientation: {w: 1.0}}}'
```
OR
```
rostopic pub /mobile_base_controller/cmd_vel geometry_msgs/Twist "linear:
  x: 0.5
  y: 0.0
  z: 0.0
angular:
  x: 0.0
  y: 0.0
  z: 0.0" -r 3
```
OR
```
rostopic pub /mobile_base_controller/cmd_vel geometry_msgs/Twist -r 3 -- '[0.5,0.0,0.0]' '[0.0, 0.0, 0.0]'
```

## Publish to cmd_vel directly
```
$ rostopic pub /cmd_vel geometry_msgs/Twist -r 3 -- '[0.5,0.0,0.0]' '[0.0, 0.0, 0.0]'
```

Note that the argument -r 3 specifies that the message will be published 3 times per second. 

## /tf
- for frames transformation, essentially either to listen to or publish transformation information.

## AMCL
- amcl is a probabilistic localization system for a robot moving in 2D. 
It implements the adaptive (or KLD-sampling) Monte Carlo localization approach, which uses a particle filter to track the pose of a robot against a known map.

##  Overview of whole system frames 
```
$ rosrun tf view_frames
$ evince frames.pdf
```

## To create a package
```
$ catkin_create_pkg tutorial rospy roscpp 
```

## For remapping between 2 topics
```
$ <remap from="/cmd_vel" to="/jetbot/cmd_vel"/>
```
- P.S: when you want to add this line into the launch file, make sure it's at the top first thing for it to work

## To publish into cmd_vel use
```
$ rostopic pub /cmd_vel geometry_msgs/Twist -r 10 -- '[0.2, 0.0, 0.0]' '[0.0, 0.0, 0.0]'
```

## To navigate into a specific ros package without knowing it's actual path
```
$ roscd package_name
```

## To kill a node
```
$ rosnode kill /topic_name
```
P.S: Kill a node (note: if the launch file that created the node has "respawn=true", the node will automatically restart after it is killed)

## To run your node, ensure your python script is executable
```
$ chmod +x gui.py
```

## Rqt Graph
We can also see the structure of how topics are passed around the system: 
```
$ rosrun rqt_graph rqt_graph
```

## Logging Tools
```
ROS_INFO()
ROS_DEBUG()
ROS_WARN()
ROS_FATAL()
```

## Rqt Plot
rqt_plot lets you visualize scalar data published to ROS topics:
```
$ rosrun rqt_plot rqt_plot
```

# Diagnose:
```
roswtf
```

- If when running rosrun for a package, and node in python isn't executable, go out to the catkin_workspace and run source dev/setup.bash,
then run: 
```
$ chmod +x node_python.py
```

## To create a new package run
```
$ catkin_create_pkg package_name python_dependencies
```

## To get a rostopic list for a specific package run
```
$ rostopic list /move_base
```

## To check if move_base is finished, run
```
$ rostopic echo /move_base/status
```

## Log Files
```
$ rosclean check
$ rosclean purge
```

## Directories
- roscd package_name: navigates to package directory directly & can jump easily

## tf delays
```
$ rosrun tf tf_monitor
$ roswtf
$ tf/Debugging Tools
$ rosrun tf tf_monitor odom base_link
$ rosrun tf tf_monitor odom map
```

## To remap topic1 into topic2 cz a node is subscribing to topic1 but needs the messsage data from topic2
- There's two solutions:
1) Use the "remap" trick in the launch file, downside the topic that we're remapping from will be killed
2) Relay method: this one looks better to use, it just basically creates a separate node and subscribes/publishes to bridge those two topics 1 & 2

## RpLidar:
When running the rplidar, execute the following command first:
```
$ sudo chmod 666 /dev/ttyUSB0
```
Then run the launch file of rp_lidar

## Setting ROS Master on one PC and Subscribing with another:
- Insert the following commands into your ~/.bashrc file in your slave robot terminal:
```
export ROS_MASTER_URI=http://10.10.10.1:11311 (IP address of the master robot you want to set)
export ROS_IP=10.10.10.2 (IP addres of the slave robot which is the current one you're using)
export ROS_HOSTNAME=10.10.10.2 (IP address of the slave robot)
```
- You also can execute them each time from your terminal, but the whole idea of the bashrc is to automate that and make it by default
- When you have both machines linked to each other, make sure that your timezones/time are fully synced with each other, otherwise you'll face problems with the /tf transforms topic between the frames
- As a sanity check, you can run roscore on your slave machine and it should print that it's not the master and that it doesn't work like that
- When you have them both wire connected and tried to ping from one machine to the other, to double check run on the slave: rostopic list | you should see all the topics that exist from the master
- When launching a package on one machine like the slave, to make sure the config is well go to the master machine and run rostopic list & try to echo a topic
- After all that tests, finally go into rviz and look at the frames relationships to see if all works out well.. you might need to do some tuning etc to setup everything together  
- This approach helps parallelizing computation by a huge margin, other people go to methods such as cross-compile Ros with docker to run code on different servers and connect them all together
- If you connected the ZED camera onto a robot for example, make sure to change the values in the config file such that the camera's position (x,z) is set with respect to the center of mass.. these values can be easily changed from the launch file of the zed camera

where: first IP Address is the master and the other one is the slave

## Concepts/Lessons Learned
- setting the ros-master correctly, for dual computation
- different ros distributions should be able to work together
- ros1 isn't really made for real-time control, people use ros2/custom c++ packages for robot control
- Using Docker to Cross-Compile ROS: concept to make real-time robotics work
- Parallelization is a way to go around making computation more efficient
- Setting up Rviz on a virtual machine inside windows to visualize stuff from another robot is challenging.. you'll run into networking issues and it isn't as simple as doing it from a ubuntu machine

P.S: no need to run roscore in ros1 if you use roslaunch

## Add the following commands in your bashrc to source each time
```
$ source /opt/ros/melodic/setup.bash
$ source /home/catkin_ws/devel/setup.bash
```

## To create a catkin_workspace run
```
$ catkin_create_pkg beginner_tutorials std_msgs rospy roscpp, where rospy are ros dependencies
```

## Note
- You can only use roslaunch to launch a launch file if it's inside a package, otherwise you can just cd into the directory that has the launch file and type
```
$ roslaunch launch_file_name.launch
```

- If you don't need the odom frame anymore from the zed camera.. you can turn of the tf_publish from the launch file of the zed camera .. but to link the odom from the magni with the map frame run the following command:
$   <node pkg="tf" type="static_transform_publisher" name="map_to_odom" 
    args="0.0 0.0 0.0 0 0 0.0 /map /odom 100" />
(inside the launch file)

In other words, the static_transform_publisher is used to manage the relationships between different frames and is an important tool when defining relationships between different frames

## RQT Reconfigure:
- If you want to tune the parameters from a visual GUI, just run the following command:
```
$ rosrun rqt_reconfigure rqt_reconfigure
```
- A window will pop-out with most of your important parameters that you want to tune

- ROS Melodic and ROS Kinetic can actually work together!

- NB: 100ms is 10Hz

## Static Transform Publisher
- Super important toolkit to define relationships in between frames

## Rviz for loading a saved rviz configuration
```
rosrun rviz rviz -d <config_name.rviz>
```
OR
```
rosrun rviz rviz -d 'rospack find package_name'/rviz/config_name.rviz
```

## When losing the magni-board, run the following command
```
$ sudo systemctl restart magni-base
```

## To control a robot manually, you can use two of the following methods:
1) Teleop Twist Keyboard
2) Joy Stick

## ROSdep:
rosdep is a command-line tool for installing system dependencies.

## Kill Nodes:
```
$ rosnode kill -a
```
or 
```
$ rosnode kill --all
```

## To install missing dependencies, run
```
$ cd ~/catkin_ws
$ rosdep install --from-paths src --ignore-src -r -y
```

## ROS::spin():
- spin() just lets all the callbacks get called for your subscribers

## catkin make for one package to debug/compile faster:
```
$ catkin_make --pkg pointcloud_to_laserscan
```

## ROS Node Kill:
```
$ rosnode kill -a # kill all node
$ rosnode kill --all # kills all nodes
$ rosnode cleanup # kill nodes that cannot be contacted!
```

## Log info from ROS topic:
```
$ self.get_logger().info('Publishing R1: "%s" % msgr1.data)
```

## ROS Melodic Cheatsheet:
- You will need to set the env variable ROS_PYTHON_VERSION to 3 when building to force python 3 otherwise by default it picks python 2.

## Navigating the ROS Package System
```
$ rospack list
$ rospack find [package_name]
```
- ex:
```
$ rospack find roscpp
>> YOUR_INSTALL_PATH/share/roscpp
>> /opt/ros/kinetic/share/roscpp # if you installed ROS kinetic from apt-get

$ roscd <package-or-stack>[/subdir]
```
- ex1:
```
$ roscd roscpp
$ pwd 
>> YOUR_INSTALL_PATH/share/roscpp # should be same path of rospack find
```
- ex2:
```
$ roscd roscpp/cmake
$ pwd
>> YOUR_INSTALL_PATH/share/roscpp/cmake
$ roscd log # roscd log will take you to the folder where ROS stores log files. Note that if you have not run any ROS programs yet, this will yield an error saying that it does not yet exist.
$ rosls <package-or-stack>[/subdir]
```
- ex:
```
$ rosls roscpp_tutorials
>> cmake launch package.xml  srv
```
## Setting Permissions for Executables:
- Right click on your script and chose "Properties -> Permissions -> Allow" executing file as program, leaves you with the exact same result as the command in terminal.
```
$ sudo chmod +x [file_name]
$ sudo chmod +x /opt/ros/melodic/share/explore_lite
```

## Clean the Package Dependencies:
```
$ rosclean purge
```

## Delete ROS Package:
```
$ sudo apt-get remove ros-fuerte-package_name
```

## Debugging:
- if you have a lot of trouble trying to build a ROS package like the "explore_lite" package .. try installing/building it on a VM first.

## ROS Kinetinc on Ubuntu 20.04:
- In order to use ROS kinetic on Ubuntu 20.04, you can install Docker image and setup the docker file.

## Display the values of Environment Variables of ROS:
```
$ printenv | grep ROS 
```

## Static Transform into URDF:
- When you have lots of static transforms, its better to move on and define all the relationships inside a urdf file .. straightforward and similar setup

## ROS Bag:
- The only commands you really need are:
```
$ rosbag record
$ rosbag play
$ rosbag filter
```

1) Record:
- To record several specific topics:
```
$ rosbag record <topic names>
```

- To record everything:
```
$ rosbag record -a
```

- To have specified bag file names:
```
$ rosbag record -0 <output file name>
```

2) Play:
- Play a rosbag (ensure roscore is active!)
```
$ rosbay play <bag_file_dir>
```

3) Filter:
- Make a new rosbag, filtering out messages that don't match the Python expression:
```
$ rosbag filter <bag_file> <output_bag_file> "<some python expressions>"
```

## ros::spin()
- spin() just lets all the callbacks get called for your subscribers. Your example code doesn't have a subscriber so you wouldn't need spin() in that case.
- But when you do have a subscriber, all of your code runs then you put a spin() at the end to keep the program from just exiting when it reaches the end of main().
- Instead of exiting, a loop continuously runs to allow the callbacks to be called when a new message arrives. To be clear, ROS will not process any callback until spin() is called.

## ROS Nodelets
- Regular nodes share data by passing messages over TCP.
- Nodelets share data by sharing a pointer to a block of memory.
- They use pointers for messages like PointCloud, LaserScan, Images

## ROS Logs
```
$ rosclean check: to check how many logs
$ rosclean purge: to clean all extra logs
```

## geometry_msgs:
- PoseStamped
- Twist (Vx/Vy/Vz & Wx/Wy/Wz)
- Pose
- Quaternion
- Pose2D 
- OccupancyGrid:  This represents a 2-D grid map, in which each cell represents the probability of occupancy.

## sensor_msgs:
- LaserScan
- PointCloud
- PointCloud2
- Imu

## nav_msgs:
- Odometry
- GetMap
- Path
- LoadMap
- GetPlan
- GridCells

## diagnostics_msgs:
- DiagnosticArray
- DiagnosticStatus
- KeyValue
- AddDiagnostics
- SelfTest

## actionlib_msgs:
- GoalID
- GoalStatus
- GoalStatusArray

## Note:
- Some ROS packages can support all different distributions, when they only use the core features of ROS that already overlap over all distros.

## Packages:
- teleop_twist_keyboard
- diff_drive_controller
- amcl
- pointcloud to laserscan
- rviz
- move base
- rplidar
- map_server
- orb slam2
- cmd_vel
- ros_jetbot
- robot state publisher
- tf
- tf monitor
- roswtf
- urdf
- RTAB: for stereo vision mapping
- ubiquity board
- amcl: adaptive monte-carlo localization
- explore_lite
- rrt exploration
- frontier exploration
- ROS bridge server
- ROS bridge websocket
- actionlib: The actionlib stack provides a standardized interface for interfacing with preemptable tasks.
Examples of this include moving the base to a target location, performing a laser scan and returning the resulting point cloud, detecting the handle of a door, etc

## Concepts:
- Bayes Theorom, Bayesian Modelling
- Occupancy Grid Cell, Probabilistic Occupancy Cell
- Sensor Models, Vehicle Models, Belief Maps

## Algorithms:
1) RRT, RRT*:
- A rapidly exploring random tree (RRT) is an algorithm designed to efficiently search nonconvex, high-dimensional spaces by randomly building a space-filling tree.
2) A*, D*
3) Bug Algorithms: Bug[0-2], Tangent Bug
4) Graph Search (fixed graph):
- Depth-First, Breadth-First, Dijkstra, A-star, Greedy best-first
5) Sampling-based Search (Build Graph):
- Probabilistic Road Maps, Rapidly-exploring Random Trees
6) Optmization (local search):
- Gradient Descent, Potential Fields, Wavefront

## ROS: Indigo, Kinetic (16.04), Melodic (18.04), Noetic (20.04)
ROS1 Melodic + Ubuntu 18.04 + Python2
ROS1 Noetic + Ubuntu 20.04 + Python3
ROS2 Foxy + Ubuntu 20.04 + Python3

- ROS Melodic and Kinetic seem to work together with the Kinetic set as the master node and the melodic as the slave

## Ubuntu Versions with ROS Distro's:
Ubuntu 14 (aka Trusty) == ROS Indigo
Ubuntu 16 (aka Xenial) == ROS Kinetic
Ubuntu 18 (aka Bionic) == ROS Melodic
Ubuntu 20 (aka Focal) == ROS Noetic

## ROS Melodic vs. Noetic:
1) Python3 in Noetic
2) Gazebo 11 in Noetic .. while ROS Melodic uses Gazebo 9
3) CMake 3.16 for noetic vs. CMake 3.10.2 in Ubuntu 18.04 (min required cmake of 3.0.2)

## ROS1 vs ROS2 Difference:
https://roboticsbackend.com/ros1-vs-ros2-practical-overview/

1) Writing Nodes: The ROS API - rclcpp, rclpy:
- In ROS1, for Cpp you use roscpp, and for Python, rospy. Both libraries are completely independent and built from scratch.
- It means that the API is not necessarily the same between roscpp and rospy, and some features are developed for one, and not the other.
- ROS2 has more layers. There is only one base library, named rcl, and implemented in C. This is the foundation which contains all of the ROS2 core features.
