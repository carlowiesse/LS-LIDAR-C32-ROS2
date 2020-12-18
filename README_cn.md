## 描述
	**本版本只验证了机械32线雷达双端口，单双回波，垂直角度均匀1度和0.33度**
	**驱动用ros2进行开发，支持ubuntu18.04, ubuntu20.04下运行**
## 建立工作空间
```
mkdir -p ~/lidar_ws/src
cd ~/lidar_ws/src
tar –xvf lidar_c32_V2.01.tar
```
## 编译打包
```
cd ~/lidar_ws
colcon build
```	
	
## 运行: 
```
source install/setup.bash
ros2 launch lidar_c32_decoder lidar_c32_launch.py
```



## lidar_c32.yaml配置文件说明: 
~~~xml
	device_ip: 192.168.1.206	//设置为雷达对应的IP
	msop_port: 2366	//数据包对应的端口
	difop_port: 2367	//设备包对应的端口
	rpm: 600	//设置为雷达对应的转速，600表示1分钟600转
	frame_id: laser_link	//设置rviz中Fixed Frame的名称
	add_multicast: false	//关闭组播
	group_ip: 224.1.1.2	//组播IP设置
	min_distance: 0.15	//距离小于0.15米的点不显示
	max_distance: 150.0	//距离大于150米的点不显示
	scan_start_angle: 1000.0	//只显示从10度到300度范围的点
	scan_end_angle: 30000.0
	distance_unit: 0.25		//距离单位为0.25cm
    degree_mode: 1	//1 表示垂直角度均匀1度,2 表示垂直角度均匀0.33度
	return_mode: 1	//1 表示单回波,2 表示双回波
	time_synchronization: false	//false表示使用电脑本地时间,true表示使用GPS时间
	publish_scan: true	//true表示开启scan点云显示
	scan_num: 15	//15表示显示第15条线对应的scan点云
	config_vert: true	//开启垂直角度校准
~~~







