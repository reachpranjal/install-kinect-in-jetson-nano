## Installing Microsoft Kinect 360 (Model 1410) in Jetson Nano

1. Check if Kinect is detected 
`$ lsusb`

2. 
```bash
$ git clone https://github.com/OpenKinect/libfreenect.git
$ sudo apt-get install git cmake build-essential libusb-1.0-0-dev freeglut3-dev libxmu-dev libxi-dev
```
3.
