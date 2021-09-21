# Communicate between several machines

## 1) Multicast domain

First, you need to be on the same multicast domain to allow communication. ```ifconfig``` can gives you information about your IP and multicast address.

## 2) ROS_DOMAIN_ID

The second constraint to communicate between machines is to be on the same ROS_DOMAIN_ID. This is a environment variable which is set at 0 by default, and you can change it like this ```ROS_DOMAIN_ID=XX``` and it will change it in your terminal.

## 3) Test it

Open one terminal by computer. On the first one, type :
```
ROS_DOMAIN_ID=6 ros2 run demo_nodes_cpp talker
```
and on the other one, type :
```
ROS_DOMAIN_ID=6 ros2 run demo_nodes_cpp listener
```
You should see the _talker_ saying something, and the _listener_ hearing this thing. (6 is for the exemple)


----------------------------

More details here : https://docs.ros.org/en/foxy/Concepts/About-Domain-ID.html
