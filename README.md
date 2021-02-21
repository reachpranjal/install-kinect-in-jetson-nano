## Installing Microsoft Kinect 360 (Model 1410) in Jetson Nano

1. Check if Kinect is detected 
`$ lsusb`

2. 
```bash
$ git clone https://github.com/OpenKinect/libfreenect.git
$ sudo apt-get install git cmake build-essential libusb-1.0-0-dev freeglut3-dev libxmu-dev libxi-dev
```
3.
```bash
$ cd libfreenect/
$ mkdir build
$ cd build
$ cmake ..
$ make -j4
```
4.
```bash
$ sudo make install
$ sudo ldconfig /usr/local/lib
```
5.
```bash
$ freenect-regview
```
6.
```bash
$ cd ~/libfreenect/src
$ python fwfetcher.py
$ mkdir ~/.libfreenect
$ cp audios.bin ~/.libfreenect/audios.bin
$ sudo freenect-micview
```
7.
```bash
$ sudo freenect-glview
```
8.
```bash
$ cd ~/catkin_ws/src/
$ git clone https://github.com/ros-drivers/freenect_stack.git
$ cd ..
$ catkin_make
$ cd
```
9. `Resource not found: rgbd_launch`
```bash
$ sudo apt-get install ros-melodic-rgbd-launch
$ roslaunch freenect_launch freenect.launch
```
10.
```bash
$ rviz
```
Select \
Fixed Frame= `camera_link` \
PointCloud2 topic= `/camera/depth_registered/image`
