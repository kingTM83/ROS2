# BASICS of ROS2

Here is all the basics of ROS2. Take the time to read this page, it will be important to you.
I will try to doc everything useful for us, but if you want to learn more, take a look to the real (long) doc here https://docs.ros.org/en/foxy/index.html.

## Workspace
A ROS workspace is a directory with a particular structure. Commonly there is a ```src``` subdirectory. Inside that subdirectory is where the source code of ROS packages will be located. A trivial workspace might look like:
```
workspace_folder/
    src/
      package_1/
          CMakeLists.txt
          package.xml

      package_2/
          setup.py
          package.xml
          resource/package_2
      ...
      package_n/
          CMakeLists.txt
          package.xml
```

## Packages

A package can be considered a container for your ROS 2 code. The minimum required contents:

  - *package.xml* file, containing meta information about the package.
  - *CMakeLists.txt* file, that describes how to build the code within the package (when using C++).

To create a package, run this command : 
```ros2 pkg create --build-type ament_cmake <package_name>```

Do not hesitate to run ```ros2 pkg -h``` to understand all other commands.

## Build

Colcon is the tool used to build your workspace. **In the root of the workspace**, run ```colcon build```.

You can select which package you want to build, to avoid you to rebuild the whole project everytime, by using the the parameter     ```colcon build --packages-select <package_name>```.

Everytime you build, you have to source the environment with ```source install/setup.bash```. (in all current/new terminals)

---------

## Nodes

Each node in ROS can send and receive data to other nodes via topics, services, actions, or parameters.

![Node](https://docs.ros.org/en/foxy/_images/Nodes-TopicandService.gif)

A full robotic system is comprised of many nodes working in concert. In ROS 2, a single executable (C++ program, Python program, etc.) can contain one or more nodes.

A node may publish data to any number of topics and simultaneously have subscriptions to any number of topics.

Do not hesitate to run ```ros2 node -h``` to understand the two commands available (info and list).

## Topics

Topics are a vital element of the ROS graph that act as a bus for nodes to exchange messages.

![Topic](https://docs.ros.org/en/foxy/_images/Topic-MultiplePublisherandMultipleSubscriber.gif)

Topics are one of the main ways in which data is moved between nodes and therefore between different parts of the system.
This is a *publish/subscribe model*. It means that when a node publish, **everyone** who is subscribed to this topic will instantly receive the data.

If you run for exemple the previous test (in INSTALL), and in another terminal you run ```rqt_graph```, you will see your nodes, communicating thanks to a topic (named /chatter).

If you do ```ros2 topic -h```, you wil see a lot of commands. We will describe some.

  - ```ros2 topic echo``` : Listen to the topic. If it receive a message, it will display on your screen.
  - ```ros2 topic list``` : List all topics running (= having at least 1 subscriber or 1 publisher).
  - ```ros2 topic info [--verbose]``` : Gives you information about the topic. With the verbose parameter, you can learn a lot more about publishers and subscribers.
  - ```ros2 topic pub``` : Allows you to publish something to the topic.

Again, do not hesitate to dig more with the ```-h``` parameter. This is one of the most useful part, so it's really important to understand topics.

## Service

Basically, this is exactly the same thing than a Topic. The only difference is about the model, here this is more like a
*call/response model*. When someone publish to a service, the subscribers have to **ask** to receive data.

## Basic commands

We've seen some important commands, like ```ros2 node```, ```ros2 topic```, or ```ros2 pkg```, but there is still more commands very useful :

  - ```ros2 run``` : Run a package specific executables.
  - ```ros2 launch``` : Run a launch file, which contains several executables.

