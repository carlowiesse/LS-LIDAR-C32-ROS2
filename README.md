## Describe:
	**This version only verifies the mechanical 32 line radar with dual ports, single and double echoes, vertical angle of 1 degree and 0.33 degree**
	**The driver is developed with ros2, and supports running under Ubuntu 18.04, and Ubuntu 20.04**

## Set up the workspace
```
mkdir -p ~/lidar_ws/src
cd ~/lidar_ws/src
tar –xvf lidar_c32_V2.01.tar
```

## Compile and package
```
cd ~/lidar_ws
colcon build
```	

## Run
```
source install/setup.bash
ros2 launch lidar_c32_decoder lidar_c32_launch.py
```



## lidar_c32.yaml Configuration file description: 
~~~xml
	device_ip: 192.168.1.206	//Set to the corresponding IP of radar
	msop_port: 2366	//The port corresponding to the data packet
	difop_port: 2367	//The port corresponding to the device package
	rpm: 600	//Set to the speed corresponding to radar, 600 means 600 rpm in 1 minute
	frame_id: laser_link	//Set the name of the fixed frame in rviz
	add_multicast: false	//false means Turn off multicast
	group_ip: 224.1.1.2	//Multicast IP settings
	min_distance: 0.15	//Points less than 0.15 meters are not displayed
	max_distance: 150.0	//Points greater than 150 meters are not displayed
	scan_start_angle: 1000.0	//Only points from 10 to 300 degrees are displayed
	scan_end_angle: 30000.0
	distance_unit: 0.25		//The unit of distance is 0.25cm
    degree_mode: 1	//1 means vertical angle 1 degree, 2 means vertical angle 0.33 degree
	return_mode: 1	//1 means single echo, 2 means double echo
	time_synchronization: false	//False means to use the local time of the computer, and true means to use the GPS time
	publish_scan: true	//True means to turn on scan point cloud display
	scan_num: 15	//15 means The scan point cloud corresponding to the 15th line is displayed
	config_vert: true	//True meansTurn on vertical angle calibration
~~~







