# Understand Discovery Servers

Switching from the DDS (and ROS 2) default **Simple Discovery Protocol** (SDP) to eProsima’s **Discovery Server** (DS) will only have an 
effect in the discovery related **traffic**. Briefly, discovery comprises two phases: Participant Discovery Phase (PDP), and Endpoint 
Discovery Phase (EDP). Translated into ROS 2 Foxy, PDP is the phase where contexts discover each other (since Foxy, the context is 
the one holding the DDS participant, before it was held on the node), whereas EDP is where the endpoints (ROS 2 publications and subscriptions) discover each other.

**How does it do it?** The Discovery Server does it by replacing the standard peer to peer discovery by one or several Discovery Servers to which the Clients connect.

The new version of the Discovery Server (DS) **reduces the traffic** up to 93% by the means of a Server that centralizes all the PDP/EDP traffic 
(meaning Clients only send their discovery packets to the Server). It is the **Server’s job** to **redistribute** the information, with the particularity 
that it only connects Clients that **have something to say to each other**, i.e. they share a topic and have one publication and one subscription in it respectively.

SDP suffers from a further problem, which is that it entirely depends on **multicast** for the PDP phase. This makes SDP burdensome to use in networks 
where multicast does not work reliably, such as *WiFi networks*, *complex networks* with several links between publishers and subscribers, and so on. 
This is why **DS** limits the communication to **unicast**, which entails that Clients need to know where the Server is beforehand.

![DiscoveryVSSimple](https://fast-dds.docs.eprosima.com/en/latest/_images/ds_explanation.svg)


ROS 2 Command Line Interface (CLI) implements several introspection features to analyze the behaviour of a ROS 2 execution. 
These features (i.e. rosbag, topic list, etc.) are very helpful to understand a ROS 2 working network.

Most of these features use the DDS capability to share any topic information with every exiting participant. 
However, the new Discovery Server v2 implements a traffic network reduction that limits the discovery data between nodes 
that do not share a topic. This means that not every node will receive every topic data unless it has a reader in that topic. 
As most of ROS 2 CLI Introspection is executed by adding a node into the network (some of them use ROS 2 Daemon, and some create their own nodes), 
using Discovery Server v2 we will find that most of these functionalities are limited and do not have all the information.

The Discovery Server v2 functionality allows every node running as a SUPER_CLIENT, a kind of Client that connects to a SERVER, 
from which it receives all the available discovery information (instead of just what it needs). In this sense, ROS 2 introspection 
tools can be configured as Super Client, thus being able to discover every entity that is using the Discovery Server protocol within the network.
