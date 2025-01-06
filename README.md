## FAST-LIO

## 1. Prerequisites
### 1.1 **Ubuntu** and **ROS**
**Ubuntu >= 16.04**

For **Ubuntu 18.04 or higher**, the **default** PCL and Eigen is enough for **FAST-LIO to work normally**.

### 1.2. **PCL && Eigen**
PCL    >= 1.8,   Follow [PCL Installation](http://www.pointclouds.org/downloads/linux.html).

Eigen  >= 3.3.4, Follow [Eigen Installation](http://eigen.tuxfamily.org/index.php?title=Main_Page).

```
sudo apt-get install libeigen3-dev
sudo apt-get install libpcl-dev
```

### 1.3. **Livox-SDK**
```
git clone https://github.com/Livox-SDK/Livox-SDK.git
cd Livox-SDK
cd build
cmake ..
make
sudo make install
```

### 1.4. **livox_ros_driver**

```
cd
git clone https://github.com/Livox-SDK/livox_ros_driver.git ws_livox/src
cd ws_livox
catkin build or catkin_make
```
### 1.5. **hokuyo3d and livox_imu**
```
cd ~/catkin_ws/src

```



## 2. Build
If you want to use docker conatiner to run fastlio2, please install the docker on you machine.
Follow [Docker Installation](https://docs.docker.com/engine/install/ubuntu/).

### 2.1 Build from source
```
cd ~/ws_livox/src
git clone https://github.com/hku-mars/FAST_LIO.git
cd FAST_LIO
git submodule update --init
cd ../..
catkin build && catkin_make
source devel/setup.bash
```

## 3. Directly run
### 3.1 For YVT
```
cd ~/ws_livox
source devel/setup.bash
roslaunch fast_lio mapping_yvt.launch
```
### 3.2 PCD file save

Set ``` pcd_save_enable ``` in launchfile to ``` 1 ```. All the scans (in global frame) will be accumulated and saved to the file ``` FAST_LIO/PCD/scans.pcd ``` after the FAST-LIO is terminated. ```pcl_viewer scans.pcd``` can visualize the point clouds.

*Tips for pcl_viewer:*
- change what to visualize/color by pressing keyboard 1,2,3,4,5 when pcl_viewer is running. 
```
1 is all random
2 is X values
3 is Y values
4 is Z values
5 is intensity
```