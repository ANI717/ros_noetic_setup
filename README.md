<h1 align="center">ROS Noetic Setup (Ubuntu 20.04)</h1>
<h4 align="center">Step by step method to install ROS Noetic in Ubuntu 20.04. The issues regarding "rosdep" is also resolved here.</h4>

## Install
```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
sudo apt update
sudo apt install ros-noetic-desktop-full
```
```
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```
```
printenv | grep ROS
```
```
sudo apt install python3-rosdep
sudo rosdep init
rosdep update
```

## Create Workspace
```
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/
catkin_make
```
```
source ~/catkin_ws/devel/setup.bash
```
```
echo $ROS_PACKAGE_PATH
```

## Create & Build package
```
cd ~/catkin_ws/src
```
catkin_create_pkg <package_name> [depend1] [depend2] [depend3]
```
catkin_create_pkg beginner_tutorials std_msgs rospy roscpp
```
```
. ~/catkin_ws/devel/setup.bash
```
```
Edit "/catkin_ws/src/beginner_tutorials/package.xml" file
```
```
cd ~/catkin_ws
catkin_make
```

## Basic Commands
```
roscore
```

rosrun [package] [node]
```
rosrun turtlesim turtlesim_node
```
rosrun [package] [node] __name:=[assigned_new_node_name]
```
rosrun turtlesim turtlesim_node __name:=my_turtle
```

rospack depends [package]
```
rospack depends turtlesim
```
rospack depends1 [package]
```
rospack depends1 turtlesim
```

```
rosnode -h
rosnode list
rosnode cleanup
```

```
rostopic -h
rostopic list
rostopic list -v
```
rostopic info [topic]
rostopic echo [topic]
rostopic type [topic]

rosmsg show [topic type]

```
rostopic pub -h
```
rostopic pub [topic] [msg_type] [args]
```
rostopic pub -1 /turtle1/cmd_vel geometry_msgs/Twist -- '[2.0, 0.0, 0.0]' '[0.0, 0.0, 1.8]'
```

rostopic hz [topic]
```
rostopic hz /turtle1/pose
```

```
rosrun rqt_graph rqt_graph
rosrun rqt_plot rqt_plot
```

```
rosservice -h
rosservice list
```

```
rosservice type [service]
rosservice type /clear
```

rosservice call [service] [args]
```
rosservice call /clear
rosservice call /spawn 2 2 0.2 ""
```

```
rosparam -h
rosparam list
```

rosparam get [param_name]
```
rosparam set /turtlesim/background_r
rosparam get /
```

rosparam set [param_name] <values>
```
rosparam set /turtlesim/background_r 150
rosservice call /clear
```
  
rosparam dump [file_name] [namespace]
```
rosparam dump params.yaml
```

rosparam load [file_name] [namespace]
```
rosparam load params.yaml copy_turtle
```
