[中文版本使用说明](<https://github.com/RichbeamTechnology/Lakibeam_ROS1_Driver/blob/main/README_CN.md>)

# 1 About the Driver

LakiBeam ROS1 Drvier is the software development kit for: LakiBeam1S/LakiBeam1/LakiBeam1L LiDAR manufactured by Richbeam (Beijing) Technology. After launched, the Driver will monitor UDP packets from Lidar, parse data and publish point clouds frames into ROS under topic: /scan or topic: /pcd.

# 2 Environment and Dependencies

System environment requirement: Linux + ROS  
Recommanded: Ubuntu 16.04 - with ROS kinetic desktop-full installed or  
Ubuntu 18.04 - with ROS melodic desktop-full installed or  
Ubuntu 20.04 - with ROS noetic desktop-full installed.  

Check resources on http://ros.org for installation guide.

# 3 Installation
1. Create the workspace for ROS1 Driver:
