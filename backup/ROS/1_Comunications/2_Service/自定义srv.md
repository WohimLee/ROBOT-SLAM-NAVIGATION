&emsp;
# 自定义 srv

在 package 文件夹下创建 /srv 文件夹

>/srv/service_msg.srv
```c++
int32 num1
int32 num2
---
int32 sum
```

>CMake 配置
```cmake
find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
  message_generation # 添加这个
)

## Generate services in the 'srv' folder
add_service_files(
  FILES
  service_msg.srv # 自定的服务消息文件
)

catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES test_pkg
 CATKIN_DEPENDS roscpp rospy std_msgs message_runtime # 添加 message_runtime
#  DEPENDS system_lib
)
```

编译完成后：
- 会在 devel/include/test_pkg 下生产 3 个头文件
    - [自定义srv].h
    - [自定义srv]Request.h
    - [自定义srv]Reponse.h

- 会在 devel/lib/python2.7/dist-packages 下生成 srv 文件夹
