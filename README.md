## 1 推荐编译环境
- ubuntu 18.04 
- ROS Melodic
- vscode or Clion 




## 3 运行相关命令

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

### 进行重定位

`roslaunch cartographer_ros demo_backpack_2d_localization.launch load_state_filename:=/home/zhanglei/carto_ws/b0-2014-07-11-10-58-16/buildconstriant/2d-1.pbstream  bag_filename:=/home/zhanglei/bagfiles/b0-2014-07-11-10-58-16.bag`

### 将点云pcd 文件发布为 ROS：：PointCloud2 消息见
 ` git clone https://github.com/hongyeah314/pcdtolaserscan.git`

### 如果要将对应时间戳对应PCD激光帧
将 node.h 中 SaveRange  设置为 true
