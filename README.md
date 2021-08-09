# MarvinARM
![Marvin](images/marvin.jpeg)
by Do Hyung (Dave) Kwon and Rose Gebhardt

## Requirement
```
ROS Melodic
Azure Kinect SDK
Azure Kinect Body Tracking SDK
Azure Kinect ROS driver
Openmanipulator X
```
## Installation

For ROS installation, follow the guide at this link: https://emanual.robotis.com/docs/en/platform/openmanipulator_x/ros_setup/. There are two key caveats. The first is that all instances of "kinetic" must be replaced with "melodic", as that is the proper ROS version for Ubuntu 18.04. The second is that an error may occur where a key is not found and the installation stops. If this occurs, the following commands should be executed:
sudo apt install curl # if you haven't already installed curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -

Once these commands are executed, run again the "wget" command and ROS should install properly.

OpenMANIPULATOR packages: To install the needed packages for OpenMANIPULATOR just follow the instructions on the link above. In the event that the final line throws an error, cd into the directory and execute "catkin make" on separate lines, and failing that restart the computer and try it again.

Azure Kinect SDK: To install the SDK, follow the instructions at this link: https://docs.microsoft.com/en-us/azure/kinect-dk/sensor-sdk-download. You may encounter an error when setting up the Microsoft package repo where a configured file "main/binary-i386/Packages" will not be acquired as the microsoft repo does not support the i386 architecture. To fix this, open the file located at "/etc/apt/sources.list" in an editor, scroll down to where the Microsoft URL is located, and in between the "deb" and the start of the link insert "[arch=amd64]". Then rerun "sudo apt-get update" and it should work fine now.

After setting up the Microsoft repo, it's time to install the Azure SDK. However, we will not be executing the base command given in the tutorial as that command installs the newest version of libk4a, which is incompatible with the ROS driver. Instead run "sudo apt install k4a-tools=1.3.0". This version will work properly with the ROS driver.

cd ~/catkin_ws/src
git clone https://github.com/thedavekwon/MarvinARM.git
rosdep install --from-paths MarvinARM --ignore-src -r -y
cd ~/catkin_ws
catkin_make


### Install rosdep 
```
# ROS Noetic
sudo apt-get install python3-rosdep
# ROS Melodic and earlier
sudo apt-get install python-rosdep
```
## Usage
```
roslaunch mimic mimic.launch

# for launching gazebo
roslaunch mimic mimic_gazebo.launch
```
## Sources
1. [ROBOTIS-GIT/open_manipulator](https://github.com/ROBOTIS-GIT/open_manipulator)
2. [microsoft/Azure_Kinect_ROS_Driver](https://github.com/microsoft/Azure_Kinect_ROS_Driver)
