# How to use RQt

RQt is a GUI for ROS, utilizing the Qt framework, that implements various tools and interfaces in the form of plugins.

If you can't run rqt with the command ```rqt```, just re-install it ```sudo apt install ros-foxy-rqt*```.

------------------

### Run RQt

The method is to run ```rqt``` and use the **GUI**. You can see in the **plugin tab** all plugins and tools available. It gives you a lot of information about your system, 
and there are a lot of plugins very useful (to see graphs, or to see what's inside your topics for exemple).


------------------

### Tools and Plugins

Here is the description of all plugins that you can find in the *Plugins* tab.

#### Action

  - *Action Type Browser* : Provides a feature to introspect all available ROS action types.

#### Configuration

  - *Dynamic Reconfigure* : Provides the way to view and edit the parameters that are accessible via dynamic_reconfigure.

#### Introspection

  - *Node Graph* : Provides a GUI plugin for visualizing the ROS computation graph. This one is pretty useful.
  - *Process Monitor* : A process monitoring utility similar to Ubuntu's System Monitor, which only shows info about ROS processes. 

#### Logging

  - *Console* : Displaying and filtering ROS messages.

#### Miscellaneous Tools

  - *Python Console* : Interactive Python console.
  - *Shell* : Interactive command line shell.

#### Services

  - *Service Caller* : Calls arbitrary services and shows the response.
  - *Service Type Browser* : Viewer to introspect the ROS services available on the system.

#### Topics

  - *Message Publisher* : Publishes arbitrary messages with fixed or computed field values.
  - *Message Type Browser* : Viewer to browse the ROS messages available on the system.
  - *Topic Monitor* : Displays debug information about ROS topics including publishers, subscribers, publishing rate, and ROS Messages.

#### Visualization

  - *Image View* : Displaying images/videos using image_transport.
  - *Plot* : Visualizes numeric values in a 2D plot.

