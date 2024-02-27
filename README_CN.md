[README](<https://github.com/RichbeamTechnology/Lakibeam_ROS1_Driver/blob/main/README.md>) - English Version of the readme

# 1 关于此驱动

Lakibeam ROS SDK 由锐驰智光（北京）科技有限公司针对LakiBeam1S/LakiBeam1/LakiBeam1L激光雷达开发。启动后，该驱动将监听雷达发送的UDP数据包，解析数据并将点云发布到 ROS 的/scan 或/pcd 话题中。

# 2 环境和依赖关系

系统环境要求：Linux+ROS
推荐：Ubuntu 16.04 - with ROS kinetic desktop-full installed 或  

Ubuntu 18.04 - with ROS melodic desktop-full installed 或

Ubuntu 20.04 - with ROS noetic desktop-full installed。

Ubuntu 安装指南请参考 http://ros.org 上的资源。

# 3 安装 ROS 驱动
## 3.1 创建工作空间
```
cd~
mkdir -p catkin_ws/src
```
## 3.2 编译
在 Lakibeam ROS Driver 目录中，执行以下指令编译工程:
```
git clone https://github.com/RichbeamTechnology/Lakibeam_ROS1_Driver.git
cd catkin_ws/src
catkin_make
```

# 4 配置电脑 IP 地址

当通过 RJ45 网线和直流电源连接时，LakiBeam1(L/S)的 IP 地址默认为 192.168.198.2，其目标计算机的 IP 地址为 192.168.198.1。所以我们需要将 PC 静态 IP 设置为 "192.168.198.1"，子网掩码设置为 "255.255.255.0"，网关地址为非必填项。配置完成后，我们可以使用 "ifconfig" 命令来检查 IP 是否可以工作。

当使用 USB Type-C 连接时，LakiBeam1(L/S)的 IP 地址默认为 192.168.8.2，计算机的 IP 地址配置为 "192.168.8.1"，连接雷达与 PC 的网络适配器的静态 IP 则不需要设置。输入以下 IP 到 web 浏览器：192.168.8.2，即雷达的 IP 地址。然后设置主机 IP为 "192.168.8.1"，并设置网络模式为 DHCP 模式并保存设置。雷达将在几秒钟延迟后重置网络配置。

雷达的 web 页面上通过 USB Type-C 进行的 IP 配置如下图所示：

![image](https://github.com/RichbeamTechnology/Lakibeam_ROS1_Driver/assets/158011589/09c012cb-5c99-4fb3-996d-7c98fd5fa67b)

# 5 launch 文件

在从雷达接收数据之前，我们应根据需要在 launch 文件中配置参数。可配置的参数如下表所示：
| 参数名称     | 配置说明     | 
| -------- | -------- |
| inverted | 翻转雷达，“true”为被翻转 |
| hostip | 目标 IP 地址，当设置为 0.0.0.0 时，可监听到所有 IP 地址 |
| port | 在一台电脑上使用双雷达时，监听端口必须与雷达 WebSever 上设置的端口号相同 |
| angle_offset | 点云绕 z 轴的旋转角度，可以设置为负数 |

# 6 查看实时数据

1. 通过 RJ45 网口和直流电源或 USB Type-C 线将 LakiBeam1(L/S)连接到 PC 上并通电。
2. 驱动内提供了几个标准的launch文件，例如 "lakibeam1_scan.launch" 和"lakibeam1_scan_view.launch"。要启动 LaserScan 节点，我们可以运行带有 scan 名称的 launch 文件来查看实时点云数据。打开终端：
```
cd ~/catkin_ws
source devel/setup.bash
roslaunch lakibeam1 lakibeam1_scan.launch
(run LaserScan node)
roslaunch lakibeam1 lakibeam1_scan_view.launch
(run LaserScan node in Rviz)
```
Rviz 中 运行 LaserScan 节点时的实时点云数据如下图所示：

![image](https://github.com/RichbeamTechnology/Lakibeam_ROS1_Driver/assets/158011589/abc00271-4baa-4199-8d2f-84da174eb824)
