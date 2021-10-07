# Which transport is used in ROS2

  Basically, ROS2 use a **DDS**, a *data distribution service*, which directly takes care of the **transport** part and which is hidden in the layers of abstraction.
  The DDS will take care of the **communication**, ROS2 have set one by default (*FastDDS eProsima*) and depending on your applications, you can change it, 
  but it is already quite advanced use.
  
  ## RTPS

DDS uses the **RTPS** protocol (*Real Time Publish-Subscribe*). [Doc](https://www.eprosima.com/index.php/resources-all/whitepapers/rtps)

RTPS is a protocol for **best effort** and **reliable** pub-sub communications over **unreliable transports such as UDP** in both unicast and multicast.


With the right set of Quality of Service policies, ROS 2 can be as **reliable** as TCP or as **best-effort** as UDP, with many, many possible states in between. ROS2 benefits from the **flexibility** of the underlying DDS transport in environments with lossy wireless networks where a *“best effort”* policy would be more suitable, or in real-time computing systems where the right Quality of Service profile is needed to meet deadlines.

