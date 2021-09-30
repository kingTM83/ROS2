# Which transport is used in ROS2

  Basically, ROS2 use a **DDS**, a *data distribution service*, which directly takes care of the **transport** part and which is hidden in the layers of abstraction.
  The DDS will take care of the **communication**, ROS2 have set one by default (*FastDDS eProsima*) and depending on your applications, you can change it, 
  but it is already quite advanced use.
  
**RTPS**
