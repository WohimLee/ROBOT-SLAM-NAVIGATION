&emsp;
# 编译 ORB-SLAM2

## 1 C++11 or C++0x Compiler
We use the new thread and chrono functionalities of C++11.

&emsp;
## 2 编译安装 Pangolin（0.6）
We use Pangolin for visualization and user interface. Dowload and install instructions can be found at: https://github.com/stevenlovegrove/Pangolin.

### 安装

```shell
sudo apt install -y libglew-dev
# Get Pangolin
cd Pangolin

# Configure and build
mkdir build && cd build
cmake -D CMAKE_INSTALL_PREFIX=~/AZen/3rdparty/Pangolin0.6 ..
```

&emsp;
## 3 编译安装 OpenCV（3.2）
We use OpenCV to manipulate images and features. Dowload and install instructions can be found at: http://opencv.org. Required at leat 2.4.3. Tested with OpenCV 2.4.11 and OpenCV 3.2.

&emsp;
## 4 编译安装 Eigen3（3.1）
Required by g2o (see below). Download and install instructions can be found at: http://eigen.tuxfamily.org. Required at least 3.1.0.

https://gitlab.com/libeigen/eigen/-/releases?after=eyJyZWxlYXNlZF9hdCI6IjIwMTMtMDctMjMgMTg6NDg6MDAuMDAwMDAwMDAwICswMDAwIiwiaWQiOiIxMTE0Mjk3In0

&emsp;
## 5 编译安装

编译过程会报错：
<div align="center">
    <image src="./imgs/1.png" width = 500>
</div>
&emsp;

修改原码中 include 文件夹下的 System.h
<div align="center">
    <image src="./imgs/2.png" width = 500>
</div>
&emsp;


