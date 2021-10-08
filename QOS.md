# QoS

ROS 2 offers a rich variety of Quality of Service (QoS) policies that allow you to tune communication between nodes. 
QoS profiles can be specified for publishers, subscriptions, service servers and clients. A connection between a 
publisher and a subscription is only made if the pair has compatible QoS profiles.


The base QoS profile currently includes settings for the following policies:

#### History

  - **Keep last**: only store up to N samples, configurable via the queue depth option.
  - **Keep all**: store all samples, subject to the configured resource limits of the underlying middleware.

#### Depth

  - **Queue size**: only honored if the “history” policy was set to “keep last”.

#### Reliability

  - **Best effort**: attempt to deliver samples, but may lose them if the network is not robust.
  - **Reliable**: guarantee that samples are delivered, may retry multiple times.

#### Durability

  - **Transient local**: the publisher becomes responsible for persisting samples for “late-joining” subscriptions.
  - **Volatile**: no attempt is made to persist samples.

#### Deadline

  - **Duration**: the expected maximum amount of time between subsequent messages being published to a topic

#### Lifespan

  - **Duration**: the maximum amount of time between the publishing and the reception of a message without the message being considered stale or expired (expired messages are silently dropped and are effectively never received).

#### Liveliness

  - **Automatic**: the system will consider all of the node’s publishers to be alive for another “lease duration” when any one of its publishers has published a message.
  - **Manual by topic**: the system will consider the publisher to be alive for another “lease duration” if it manually asserts that it is still alive (via a call to the publisher API).

#### Lease Duration

  - **Duration**: the maximum period of time a publisher has to indicate that it is alive before the system considers it to have lost liveliness (losing liveliness could be an indication of a failure).


With the right set of Quality of Service Reliability, ROS 2 can be as reliable as TCP or as best-effort as UDP.

To see if pub/sub can be compatible : https://docs.ros.org/en/foxy/Concepts/About-Quality-of-Service-Settings.html#qos-compatibilities
