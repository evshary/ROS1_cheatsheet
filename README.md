# ROS1_cheatsheet

# Create simple package

How to create a simple ROS 1 package.

* Create package folder

```bash
mkdir -p example_pkg_ws/src
cd example_pkg_ws/src
catkin_create_pkg beginner_tutorials std_msgs rospy roscpp
```

* Add the code

```bash
mkdir scripts && cd scripts
wget https://raw.github.com/ros/ros_tutorials/kinetic-devel/rospy_tutorials/001_talker_listener/talker.py
cd ..
```

* Add the following line to `CmakeLists.txt`

```
catkin_install_python(PROGRAMS scripts/talker.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
```

* Build

```bash
# Back to example_pkg_ws
cd ../../
catkin_make
```

* Run

```
source devel/setup.bash
rosrun beginner_tutorials talker.py
```

# Create deb for ROS package - bloom-generate

Refer to [How to make a debian from a ROS package](https://gist.github.com/awesomebytes/196eab972a94dd8fcdd69adfe3bd1152)

* Install necessary packages

```bash
sudo apt install dpkg-dev debhelper
sudo apt install python3-bloom fakeroot
# or if you use python2
sudo apt install python-bloom fakeroot
```

* Create debian structure

```bash
roscd beginner_tutorials
bloom-generate rosdebian --os-name ubuntu --ros-distro noetic
# Will generate debian folder
fakeroot debian/rules binary
# Will create deb file in upper folder
```

* Install the package

```bash
sudo apt install ../*.deb
```

