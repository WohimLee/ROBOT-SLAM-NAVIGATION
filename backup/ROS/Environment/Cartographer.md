&emsp;
# Cartographer 环境配置

## 实验环境
- 电脑系统：Mac OS
- 工具：VMWARE Fusion
    - 虚拟机系统： Ubuntu18.04 
    - ROS 版本：Melodic
- Cartographer 官方文档：https://google-cartographer.readthedocs.io/en/latest/index.html
- Cartographer ROS 官方文档：https://google-cartographer-ros.readthedocs.io/en/latest/index.html

&emsp;
# 1 Building & Installation

## (1)  
```shell
sudo apt-get update
sudo apt-get install -y python-wstool python-rosdep ninja-build stow
```

## (2)
- 这步 `wstool merge` 可能会报错，需要改一下文件
    - ipaddress.com 查 raw.githubusercontent.com 的 ip
        <div align = center>
            <img src = "/datav/Education/9_ROS/Environment/imgs/ipaddress.png" width = 400>
        </div>
    - 添加ip `sudo vim /etc/hosts`，可能会不成功，每个ip都试一下，切换成手机热点也试一下
        <div align = center>
            <img src = "/datav/Education/9_ROS/Environment/imgs/ipaddress2.png" width = 400>
        </div>

After the tools are installed, create a new cartographer_ros workspace in ‘catkin_ws’.

```shell
mkdir catkin_ws
cd catkin_ws
wstool init src
wstool merge -t src https://raw.githubusercontent.com/cartographer-project/cartographer_ros/master/cartographer_ros.rosinstall
wstool update -t src
```

&emsp;
## (3)
Now you need to install cartographer_ros’ dependencies. First, we use rosdep to install the required packages. The command ‘sudo rosdep init’ will print an error if you have already executed it since installing ROS. This error can be ignored.
```
sudo rosdep init
rosdep update
rosdep install --from-paths src --ignore-src --rosdistro=${ROS_DISTRO} -y
```

&emsp;
## (4)
Cartographer uses the abseil-cpp library that needs to be manually installed using this script:
```
src/cartographer/scripts/install_abseil.sh
```

&emsp;
## (5)
Due to conflicting versions you might need to uninstall the ROS abseil-cpp using
```
sudo apt-get remove ros-${ROS_DISTRO}-abseil-cpp
```

&emsp;
## (6)
Build and install.
```shell
catkin_make_isolated --install --use-ninja
```
