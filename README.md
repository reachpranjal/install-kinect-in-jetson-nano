## Installing Microsoft Kinect 360 (Model 1410) in Jetson Nano

1. Check if Kinect is detected \
```bash
$ lsusb
```

2. Install libfreenect, freeglut & libxmu
```bash
$ git clone https://github.com/OpenKinect/libfreenect.git
$ sudo apt-get install git cmake build-essential libusb-1.0-0-dev freeglut3-dev libxmu-dev libxi-dev
```
3. Build using cmake
```bash
$ cd libfreenect/
$ mkdir build
$ cd build
$ cmake ..
$ make -j4
```
4. make install
```bash
$ sudo make install
$ sudo ldconfig /usr/local/lib
```
5. RGB with Depth Overlay
```bash
$ freenect-regview
```
6. Kinect built-in Audio 
```bash
$ cd ~/libfreenect/src
$ python fwfetcher.py
$ mkdir ~/.libfreenect
$ cp audios.bin ~/.libfreenect/audios.bin
$ sudo freenect-micview
```
7. Visualize audio input waves
```bash
$ sudo freenect-glview
```
8. Build freenect driver
```bash
$ cd ~/catkin_ws/src/
$ git clone https://github.com/ros-drivers/freenect_stack.git
$ cd ..
$ catkin_make
$ cd
```
9. You might come across this error- `Resource not found: rgbd_launch`
```bash
$ sudo apt-get install ros-melodic-rgbd-launch
$ roslaunch freenect_launch freenect.launch
```
10. Open rvi and visualize pointcloud
```bash
$ rviz
```
Select \
Fixed Frame= `camera_link` \
PointCloud2 topic= `/camera/depth_registered/points`
