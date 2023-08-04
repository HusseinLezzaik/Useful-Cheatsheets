## Tips for using DL on Jetson
1) Configure your Jetson device for optimal performance:

(1) `nvpmodel`
- Default mode is 5 - with 10W
- ~ 8 modes available, depending on the Jetson type

(2) `tegrastats`

(3) `jetson clocks`

2) Optimize your models runtime for Jetson:
- quantization
- pruning
- graph compilers

3) Calibrate production parameters for your inference pipeline:
- Batch Size: Unlike cloud gpus, higher is not better (IO bottlenecks, Memory swaps)
- The best combination of threads and processes for each dl model.. you can automate this process

4) Benchmark your application end-to-end pipeline:
- Test and benchmark your apps end-to-end
- Use "jtop" or other tools to monitor the real-time efficiency if the lifecycle
- Benchmark each step separately to identify bottlenecks
- Benchmark what matters
- Distinguish between object creation and memory copy.. data loading and copying might consume more than inference

5) Use concurrent code and multiple processes:
- It's hard to utilize the GPU with a single process, load several instances of the model in multiple processes
- Write multi-threaded code to maximize throughput: inference, data loading, pre/post processing
- Consider smaller batch sizes in concurrent processing
- Find the optimal pipeline for your application
- Synchronous vs. Asynchronous (concurrent code): async is like 7x faster than sync, depends on the model itself

6) Use containers to develop and test your application on Jetson:
- Double-check your JetPack version
- Don't work on the host itself
- Use containers to build and run development environments
- Use the default Python interpreter for your version
- Use a swap file
- Use "docker run --rm" for temporary containers
- Save only what you need to keep the image small, reduce image size with nested commands (...&&...)

7) Build for Jetson on Any x86 Machine:
- Enable QEMU in docker
- Build Images
- Compile software for Jetson

## Jetson SDK 4.6 steps
1. Download image from https://developer.nvidia.com/jetson-nano-sd-card-image
2. Flash SD card
3. Connect Wi-Fi
4. Update system
```
$ sudo apt update
$ sudo apt-get update
```
5. Install gcc g++
```
$ sudo apt install build-essential
$ sudo apt-get install manpages-dev
$ sudo apt install software-properties-common
$ sudo add-apt-repository ppa:ubuntu-toolchain-r/test
$ sudo apt install gcc-7 g++-7 gcc-8 g++-8
$ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-8 80 --slave /usr/bin/g++ g++ /usr/bin/g++-8 --slave /usr/bin/gcov gcov /usr/bin/gcov-8
$ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-7 70 --slave /usr/bin/g++ g++ /usr/bin/g++-7 --slave /usr/bin/gcov gcov /usr/bin/gcov-7
```
6. Install/Update python 3.6
```
$ sudo apt update
$ sudo apt install python3.6
$ sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.6 1
$ sudo update-alternatives --config python3
$ sudo apt update
$ sudo apt-get update
$ sudo apt install python-pip python3-pip
$ sudo apt install python3.6-dev
$ sudo apt-get install -y python-setuptools-scm python3-setuptools-scm
$ sudo -H pip install --upgrade pip
$ sudo -H pip3 install --upgrade pip
$ sudo -H pip install setuptools
$ sudo -H pip3 install setuptools
$ sudo -H pip3 install rospkg
```
7. Install ZED SDK
- follow instructions from [here](https://www.stereolabs.com/docs/installation/jetson/)
8. Install ROS Melodic
- follow instructions from [here](http://wiki.ros.org/melodic/Installation/Ubuntu)
- follow instructions from [here](http://wiki.ros.org/catkin/Tutorials/create_a_workspace) (python not python3)
9. `$ gedit ~/.bashrc`
10. Go to the bottom (my last line was `source /opt/ros/melodic/setup.bash` , for others it may differ). Go under that line and write --> `source ~/catkin_ws/devel/setup.bash`
11. Save and exit
12. Instal ZED Wrapper and examples
follow instructions from https://www.stereolabs.com/docs/ros/
13. Copy over our folders
```
$ sudo apt-get install ros-melodic-pointcloud-to-laserscan
$ sudo apt-get install ros-melodic-navigation
```
14. make again

## Jetson Stats
https://github.com/rbonghi/jetson_stats

## Jetson Hacks
https://jetsonhacks.com/
