# ROS_Creating a ROS Package #

***

## what makes up a catkin package ##

1. the package must contain a packge.xml file
    + package.xml file provides meta information about the package
2. the package must contain a CMakeList.txt
    + if it is a **catkin metapackage**

```
my_package/
    CMakeLists.txt
    package.xml
```

***

## crating a catkin workspace ##

+ 第一步要先 source ros 的還境

```
$ source /opt/ros/noetic/setup.bash
```

可以把這行加到 ~/.bashrc中 這樣每次開終端機都會自動執行


+ 首先要先創立一個 workspace 資料夾

```
$ mkdir -p ~/catkin_ws/src
$ cd ~/catkin_ws/src
$ catkin_make
```
當你第一次在workspace執行 **$ catkin_make** 時，它會在 src 資料夾中建立 CMakeLists.txt 檔案

## python 3 user in ROS Melodic or earlier ##

+ 當要在 workspce 中第一次執行 **$ catkin_make** 時，請用下面的指令

```
$ catkin_make -DPYTHON_EXECUTABLE=/usr/bin/pyton3
```

+ sourcing **setup.bash** in /catkin_ws/devel will overlay this workspace on top of your environment

```
$ source ~/catkin_ws/devel/setup.bash
```

+ to make sure your workspace is properly overlayed by the setup script, make sure `ROS_PACKAGE_PATH` environment variable includes the directory you're in.

```
$ echo $ROS_PACKAGE_PATH
/home/user_name/catkin_ws/src:/opt/ros/noetic/share
```

***

## crating a catkin package ##

+ 第一步 cd 到 ~/catkin_ws/src

```
$ cd ~/catkin_ws/src
```

### `＄ catkin_create_pkg <package_name> [depend1] [depend2] [depend3]` ###

+ 使用 **catkin_create_pkg** 創立 tutorial package 並加入 std_msgs roscpp rospy 的 dependency

```
$ catkin_create_pkg beginner_tutorials std_msgs roscpp rospy
```

+ 這道指令會建立 **beginner_tutorials package** 並且會自動生成
package.xml 和 CMakeLists.txt

***

## customizing your package ##

the generated **package.xml** should be in new package. 
Now lets go through the new **package.xml** and touch up any elements that need your attention.

1. description tag

```
<description>The beginner_tutorials package</description>
```
可以放入簡短的說明 package 的功能

2. maintainer tags

```
 <maintainer email="you@yourdomain.tld">Your Name</maintainer>
```

一位維護者需要一個tag

example:
```
<maintainer email="jane.doe@example.com">Jane Doe</maintainer>
```

3. license tags

```
<!-- One license tag required, multiple allowed, one license per tag -->
<!-- Commonly used license strings: -->
<!--   BSD, MIT, Boost Software License, GPLv2, GPLv3, LGPLv2.1, LGPLv3 -->
<license>TODO</license>
```
選擇 **package** 的開源方式

example:
```
<license>BSD</license>
```

4. dependencies tags

```
<!-- The *_depend tags are used to specify dependencies -->
<!-- Dependencies can be catkin packages or system dependencies -->
<!-- Examples: -->
<!-- Use build_depend for packages you need at compile time: -->
<!--   <build_depend>genmsg</build_depend> -->
<!-- Use buildtool_depend for build tool packages: -->
<!--   <buildtool_depend>catkin</buildtool_depend> -->
<!-- Use exec_depend for packages you need at runtime: -->
<!--   <exec_depend>python-yaml</exec_depend> -->
<!-- Use test_depend for packages you need only for testing: -->
<!--   <test_depend>gtest</test_depend> -->
<buildtool_depend>catkin</buildtool_depend>
<build_depend>roscpp</build_depend>
<build_depend>rospy</build_depend>
<build_depend>std_msgs</build_depend>
```
