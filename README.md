# ROS Noetic Install
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

# Create Workspace
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

# Create & Build package
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
Edit "/catkin_ws/src/beginner_tutorials/package.xml" file
```
cd ~/catkin_ws
catkin_make
```
