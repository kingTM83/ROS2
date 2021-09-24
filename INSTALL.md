# Install ROS2 (Foxy)

**IMPORTANT** Ubuntu 20.04 is needed to install Foxy.

## 1) Check your locales
Make ```locale``` and all locales *(LANGUAGE is not mandatory)* should be "....UTF-8".
If not, type :
```
sudo apt install locales
sudo locale-gen fr_FR fr_FR.UTF-8
sudo update-locale LC_ALL=fr_FR.UTF-8 LANG=fr_FR.UTF-8
export LANG=fr_FR.UTF-8
```

## 2) Setup sources
Install curl, authorize ROS's GPG key and add repository to your source list like this :
```
sudo apt install curl gnupg2 lsb-release
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key  -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

## 3) Install foxy
```
sudo apt update
sudo apt install ros-foxy-desktop
```

## 4) Setup environment

```
echo "source /opt/ros/foxy/setup.bash" >> ~/.bashrc
```

If you don't want to put this line in your bashrc, don't forget to source **everytime** you open a new terminal.

## 5) Install some useful packages

Colcon is used to build a package in ROS2.

```
sudo apt install python3-colcon-common-extensions
```

Gazebo is a leader in robot simulation.
```
sudo apt install ros-foxy-gazebo-ros-pkgs
```
--------------------
You now have ROS2 on your computer. Let's try something to test.
Open 2 terminals. In the first one, type :
```
ros2 run demo_nodes_cpp talker
```
and in the other one, type :
```
ros2 run demo_nodes_cpp listener
```
You should see the _talker_ saying something, and the _listener_ hearing this thing. Thanks!

## Bug List

* Never download 2 different versions of ROS, be careful to truely uninstall it before install another version (```sudo apt remove ~nros-foxy-* && sudo apt autoremove```).
* If something goes wrong when installing, try to update your packages by doing ```sudo apt update``` and resume.
* Any other problem is maybe solved here : https://answers.ros.org/questions/
