# How to create a custom message in ROS2

In your ```ros2_ws/src```, create a new package
```ros2 pkg create --build-type ament_cmake custom_interface``` .

In this package, you will make a new directory ```mkdir msg```, and in this directory you can create ```.msg``` files for any new type you want to create.
So for exemple, ```ros2_ws/src/custom_interface/msg/Star.msg```

And in this file, you have to respect a **pattern**, which is :
```
fieldtype1 fieldname1
fieldtype2 fieldname2
fieldtype3 fieldname3
```
In our exemple, it can be :
```
string star_name
int64 pos_x
int64 pos_y
int64 pos_z
```

Perfect. Now we have to modify *CMakeList.txt* and *packages.xml*.

In **CMakeList.txt**, add these lines :
```
find_package(rosidl_default_generators REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
  "msg/Star.msg"
 )
 ```
 
 In **packages.xml**, add these lines :
 ```
<build_depend>rosidl_default_generators</build_depend>
<exec_depend>rosidl_default_runtime</exec_depend>
<member_of_group>rosidl_interface_packages</member_of_group>
```

Now return to the root of your workspace (```cd ~/ros2_ws```), and build your project
```colcon build --packages-select custom_interface```

**Source your build** ```. install/setup.bash```

Let's try if you see your new interface with ```ros2 interface show custom_interface/msg/Star```


More info https://docs.ros.org/en/foxy/Concepts/About-ROS-Interfaces.html
