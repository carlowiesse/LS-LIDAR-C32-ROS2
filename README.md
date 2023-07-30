# ROS2 packages for using Leishen 32-channel lidars

![Foxy](https://img.shields.io/badge/foxy-E09623.svg?style=for-the-badge&logo=ros&logoColor=white)
![Galactic](https://img.shields.io/badge/galactic-0F4C81.svg?style=for-the-badge&logo=ros&logoColor=white)
![Humble](https://img.shields.io/badge/humble-66A3D9.svg?style=for-the-badge&logo=ros&logoColor=white)
![Iron](https://img.shields.io/badge/iron-7A4C1C.svg?style=for-the-badge&logo=ros&logoColor=white)

## Acknowledgements

This is a continuation of the work done by [LS-Technical-Supporter](https://https://github.com/LS-Technical-Supporter).

## Quickstart

1. Set up workspace

    ```bash
    mkdir -p ~/workspaces/lslidar_ws/ && cd ~/workspaces/lslidar_ws/
    ```

2. Clone repository

    ```bash
    git clone https://github.com/carlowiesse/LS-LIDAR-C32-ROS2.git src/lslidar
    ```

3. Install dependencies

    ```bash
    sudo apt update && rosdep install --from-paths src -y --ignore-src
    ```

4. Build and source workspace

    ```bash
    colcon build && source install/setup.bash
    ```

5. Run launch file

    ```bash
    ros2 launch lidar_c32_decoder lidar_c32_launch.py
    ```

## ROS Parameters

Available ROS launch files with their corresponding configuration files:

| Launch file                | Configuration file                   | Description                                                |
| -------------------------- | ------------------------------------ | ---------------------------------------------------------- |
| lidar_c32_launch.py        | `lidar_c32.yaml`                     | Start data registration using ROS for one lidar device.    |
| lidar_c32_double_launch.py | `lidar_c32.yaml`, `lidar_c32_1.yaml` | Start data registration using ROS for two lidar devices.   |

Available parameters for each ROS node present in the above configuration files:

### `cloud_node` parameters

| ROS Parameter                | Type     | Default         | Description                                                                                   |
| ---------------------------- | -------- | --------------- | --------------------------------------------------------------------------------------------- |
| `min_distance`               | `float`  | `0.15`          | Minimum depth distance (in meters)                                                            |
| `max_distance`               | `float`  | `150`           | Maximum depth distance (in meters)                                                            |
| `degree_mode`                | `int`    | `1`             | Whether to set the vertical resolution to be 1° (`1`) or 0.33° (`2`).                         |
| `distance_unit`              | `float`  | `0.25`          | Depth resolution (in centimeters)                                                             |
| `return_mode`                | `int`    | `1`             | Whether to show every console output message once (`1`) or twice (`2`).                       |
| `config_vert`                | `bool`   | `true`          | Whether to use vertical angle calibration.                                                    |
| `print_vert`                 | `bool`   | `false`         | Whether to show console output from vertical angle calibration.                               |
| `scan_frame_id`              | `string` | `laser_link`    | Name of the TF frame used to display the point cloud.                                         |
| `scan_num`                   | `int`    | `15`            | Number of vertical scan lines.                                                                |
| `publish_scan`               | `bool`   | `true`          | Whether to publish the point cloud.                                                           |

### `lidar_node` parameters

| ROS Parameter                | Type     | Default         | Description                                                                                   |
| ---------------------------- | -------- | --------------- | --------------------------------------------------------------------------------------------- |
| `device_ip`                  | `string` | `192.168.1.200` | IP address corresponding to the device (lidar).                                               |
| `msop_port`                  | `int`    | `2368`          | UDP port corresponding to the data packet from the device.                                    |
| `difop_port`                 | `int`    | `2369`          | UDP port corresponding to the device package.                                                 |
| `frame_id`                   | `string` | `laser_link`    | Name of the fixed TF frame used as reference.                                                 |
| `add_multicast`              | `bool`   | `false`         | Whether to enable multicast.                                                                  |
| `group_ip`                   | `string` | `224.1.1.2`     | IP address used in multicast.                                                                 |
| `rpm`                        | `float`  | `600.0`         | Rotation speed (in revolutions per minute)                                                    |
| `return_mode`                | `int`    | `1`             | Whether to show every console output message once (`1`) or twice (`2`).                       |
| `degree_mode`                | `int`    | `1`             | Whether to set the vertical resolution to be 1° (`1`) or 0.33° (`2`).                         |
| `time_synchronization`       | `bool`   | `false`         | Whether to use local computer time (`false`) or GPS time from the device (`true`).            |
