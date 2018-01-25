VPL-16 Setup (for Ubuntu 16.04)
##########################################


Getting on the LiDAR on the Network
***************************************
The basic tutorial is `here <http://wiki.ros.org/velodyne/Tutorials/Getting%20Started%20with%20the%20HDL-32E>`_, but you may run into issues like I did. In which case, the following notes may be useful.

First figure out what the devise name is. To show all devices found:
::

	ifconfig -a

Which gives something like (desktop):
::

  febbo@febbo-HP-Z220-SFF-Workstation:~/Documents/workspace/Docs$ ifconfig -a
  eno1      Link encap:Ethernet  HWaddr b4:b5:2f:a9:52:61
            inet addr:192.168.1.200  Bcast:0.0.0.0  Mask:255.255.255.255
            inet6 addr: fe80::b6b5:2fff:fea9:5261/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:1604067 errors:0 dropped:0 overruns:0 frame:0
            TX packets:22232 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:1722487876 (1.7 GB)  TX bytes:2422647 (2.4 MB)
            Interrupt:20 Memory:f7100000-f7120000

  lo        Link encap:Local Loopback
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:65536  Metric:1
            RX packets:89494 errors:0 dropped:0 overruns:0 frame:0
            TX packets:89494 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1
            RX bytes:145501992 (145.5 MB)  TX bytes:145501992 (145.5 MB)


.. warning:: Note that the device is ``eno1``, not ``eth0``. Also, on my laptop the device name is `enp0s25`, so it is different depending on the machine.

Then do (desktop):
::

	sudo ifconfig eno1 up
	sudo ip addr add 192.168.1.200 dev eno1
	sudo route add -net 192.168.1.0 netmask 255.255.255.0 dev eno1

Then do (laptop):
::

	sudo ifconfig enp0s25 up
	sudo ip addr add 192.168.1.200 dev enp0s25
	sudo route add -net 192.168.1.0 netmask 255.255.255.0 dev enp0s25

Next got to: `Network` -> `Options`... and click `Ethernet Settings`

Ethernet Settings
------------------
Type the LiDAR's cloned MAC address in the box.

.. note:: To find the cloned MAC address for the LiDAR; look at the bottom of the device. For me it is:
  ::

    60:76:88:10:47:F9

.. warning::  If you are trying to get the Internet back delete the MAC address in the box.

Now you can change the name of the network to something, perhaps `LiDAR`.


Testing the LiDAR
***********************

First clone the Velodyne LiDAR ros package into a ``catkin_ws``:
::

  git clone http://wiki.ros.org/velodyne

To run it:
::

	roslaunch velodyne_pointcloud VLP16_points.launch

To view data run:
::

	rosrun rviz rviz -f velodyne

Then add try adding ``LaserScan`` and ``PointCloud2`` and their topics ``/velodyne_points`` and ``/scan``, respectively.

If you have trouble `these instructions <http://wiki.ros.org/velodyne/Tutorials/Getting%20Started%20with%20the%20HDL-32E>`_ will help you display the data in rviz.

Getting on the Computer back on the Internet
**********************************************
On the top right of your screen highlight the ``Network`` icon and click ``Edit Connections``. Then click ``Add`` add back the Internet with the following steps.

.. warning:: Make sure that you name the ``LiDAR`` connection and the ``Internet`` connection.

First go to: Network -> Options...

Ethernet Settings
------------------
.. note::  If you are trying to get the Internet back delete the MAC address in the box.

IPv4 Settings
----------------
.. note:: If you are trying to get the Internet back, select the ``Method`` to be:
  ::

    Automatic (DHCP)

MISC
*********


IPv4 Settings
----------------


    route -n
