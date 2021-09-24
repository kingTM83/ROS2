# What is rosbag2 and how to use it ?

The tool rosbag2 is part of the ROS 2 command line interfaces. There are three commands available for ```ros2 bag``` :

  - ```ros2 bag record [topics [topics...]]``` : Record all or selected topics data.
  - ```ros2 bag play {bag_file}``` : Play back data from a bag.
  - ```ros2 bag info {bag_file}``` : Print information about a bag.


## Record Data

To record all topics, use the arg ```-a```.

If not further specified, ```ros2 bag record``` will create a new folder named to the 
current time stamp and stores all data within this folder. A user defined name can be given with ```-o```, ```--output```.

By default rosbag2 will record all data into a single bag file, but this can be changed. For exemple : 
```ros2 bag record -a -b 100000``` will split the bag files when they become greater than 100 kilobytes.

By default rosbag2 does not record with compression enabled., but this can be changed. For exemple :
```ros2 bag record -a --compression-mode file --compression-format zstd```
will record all topics and compress each file using the zstd compressor.


## Play Back Data

After recording data, the next logical step is to replay this data :
```ros2 bag play <bag_file>```.

## Information about a bag

The recorded data can be analyzed by displaying some meta information about it :
```ros2 bag info <bag_file>```
