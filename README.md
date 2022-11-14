# cartographer 超详细注释代码

## 1 开源项目简介
本项目对cartographer进行了逐行的注释，代码是基于2021.04.20日在cartographer官方github上下载的master的代码

共做了如下工作
- 在代码中进行了规范, 超详细的注释, 帮助大家更好的理解源码
- 对cartographer中的关键概念进行了解释与说明
- 对cartographer中使用的**c++11新标准**语法进行了标注与说明
- 编写了编译, 保存地图相关的脚本
- 对2d建图, 3d建图, 纯定位模式进行了launch与lua文件的的配置
- 对3d的cartographer添加了实时显示三维点云地图与保存地图的功能
- **配套了逐行讲解源码的视频课程**

## 2 推荐编译环境
- ubuntu 16.04/18.04 版本
- ROS Kinetic/Melodic 版本
- vscode

vscode中推荐的插件有: 
- C/C++
- C++ Intellisense
- Doxygen Documentation Generator
- Msg Language Support
- XML Tools
- Todo Tree: 注释的高亮显示


## 3 运行相关命令

其中的bag文件可以在我的公众号: 从零开始搭SLAM  里找到，在底部菜单栏的数据集链接里

### 2d建图指令
`roslaunch cartographer_ros lx_rs16_2d_outdoor.launch`

### 保存2d轨迹,并生成ros格式的地图
`./finish_slam_2d.sh`

### 纯定位模式
`roslaunch cartographer_ros lx_rs16_2d_outdoor_localization.launch`

### 3d建图指令
`roslaunch cartographer_ros lx_rs16_3d.launch`

### 保存3d轨迹
`./finish_slam_3d.sh`

### 使用asset生成ros格式的2d栅格地图
`roslaunch cartographer_ros assets_writer_2d.launch`

### 使用asset生成3d点云地图
`roslaunch cartographer_ros assets_writer_3d.launch`

### landmark使用示例
`roslaunch cartographer_ros landmark_mir_100.launch`


## 4 实时显示三维点云地图与保存地图的功能简述
显示三维点云地图需要是在建3d轨迹的情况下才可以显示, 点云地图默认发布在 `/point_cloud_map` 话题中.

默认关闭了保存pcd格式点云的功能, 如需要这个功能, 需要将node.cc文件的第1029行的 `constexpr bool save_pcd = false;` 改成true.

编译之后在建图结束后通过调用 `/write_state` 服务, 会在生成pbstream文件的同时也对pcd文件进行保存, 保存目录与pbstream文件同一个文件夹.

个人水平有限, 如果改完的代码有问题请您联系我进行改正.

![pcd_map](src/cartographer/docs/pcd_map.png)
