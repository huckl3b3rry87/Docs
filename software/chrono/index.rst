Project Chrono
****************

Background
===========

Physics simulator organized as a set of modules that has a high-fidelity HMWWV model validated using Adams.


`Install <http://api.projectchrono.org/tutorial_install_chrono.html>`_
==========================================================================

Get the `IRRlicht engine <http://irrlicht.sourceforge.net/downloads>`_
-------------------------------------------------------------------------

Make sure that you have the required files:
::

  sudo apt-get install cmake-extras cmake-qt-gui build-essential xorg-dev freeglut3-dev

After `downloading <http://irrlicht.sourceforge.net/?page_id=10`_ unzip:
::

  sudo unzip /home/febbo/Downloads/irrlicht-1.8.4.zip -d /opt/irrlicht


Compile the ``Irrlicht Engine 1.8.4`` as a shared lib:
::

  /opt/irrlicht/irrlicht-1.8.4/source/Irrlicht$ sudo make sharedlib
  /opt/irrlicht/irrlicht-1.8.4/source/Irrlicht$ sudo make install

Chrono
-------
`Install instructions <http://www.irrlicht3d.org/wiki/?n=Main.InstallingIrrlicht>`_

Go into ``/opt`` folder:
::

  sudo mkdir chrono
  cd chrono
  sudo mkdir chrono_source
  sudo mkdir chrono_build
  cd chrono_source

Clone the master branch into the ``/opt/chrono/chrono_source`` directory:
::

  sudo git clone -b master https://github.com/projectchrono/chrono.git
  cd chrono

To configure:
::

  sudo cmake-gui

![Chrono Build](chrono_build.png)


Then to build (assuming ninja was used) go into the ``build`` directory and type:
::

  chrono/chrono_build$ sudo ninja


The rest is old....
--------------------------

`VEHICLE Module <http://api.projectchrono.org/module_vehicle_installation.html>`_
------------------



Connecting to Gazebo
--------------------
A `repo <https://github.com/amelmquist/Chrono_Gazebo>`_ was developed to connect Gazebo to Chrono.


Install
^^^^^^^^^^^
  1) `Install Gazebo 7 from source <https://github.com/amelmquist/Chrono_Gazebo>`_
  2) run:
  ::

    sudo apt-get install libogre-1.9-dev


Potential Fixes
==================
Try updating ``glib`` with:
::

  sudo apt-get update && sudo apt-get upgrade




Issues:
===========

  * https://groups.google.com/forum/#!topic/projectchrono/ETBnyS18MNM
  * https://groups.google.com/forum/#!topic/projectchrono/1GI3RiZI-2A
  * https://stackoverflow.com/questions/13978692/strcpy-sse2-unaligned-s-not-found
  * https://sourceforge.net/p/irrlicht/bugs/375/

compiler cannot find Chrono header files
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Issue might look something like:
::

  /build$ ninja
  [1/2] Building CXX object demo_Steerin....dir/demo_VEH_SteeringController.cpp.o
  FAILED: /usr/bin/c++      -MMD -MT demo_SteeringController/CMakeFiles/demo_SteeringController.dir/demo_VEH_SteeringController.cpp.o -MF demo_SteeringController/CMakeFiles/demo_SteeringController.dir/demo_VEH_SteeringController.cpp.o.d -o demo_SteeringController/CMakeFiles/demo_SteeringController.dir/demo_VEH_SteeringController.cpp.o -c /home/febbo/Documents/workspace/tutorials/chrono_tutorials/source/demo_SteeringController/demo_VEH_SteeringController.cpp
  /home/febbo/Documents/workspace/tutorials/chrono_tutorials/source/demo_SteeringController/demo_VEH_SteeringController.cpp:22:37: fatal error: chrono/core/ChFileutils.h: No such file or directory
  compilation terminated.
  ninja: build stopped: subcommand failed.

https://github.com/projectchrono/chrono/issues/79

In this case, copy the
Resources
==========

  * https://vimeo.com/uwsbel
  * http://sbel.wisc.edu/Animations/


OLD
========
NOT NEEDED::

make a build directory:
::

  src/Chrono_Gazebo/gazonoVehicle$ sudo mkdir build


set up build environment:
::

  src/Chrono_Gazebo/gazonoVehicle$ sudo cmake CMakeLists.txt

make:
::


git clone git://git.code.sf.net/p/libosmscout/code libosmscout-code


Shared Pointers
=================
http://api.projectchrono.org/shared_pointers.html

TEMP
=======
gazonoVehicle.cc


//gazebo_ros includes NOTE because ros is not in usr/include/ there are sourcing issues
#include <ros/callback_queue.h>
#include <ros/subscribe_options.h>
#include <ros/ros.h>
#include "boost/thread/mutex.hpp"
#include <std_msgs/Float64.h>


Issue:

/usr/bin/ld: cannot find -lpthreads

https://stackoverflow.com/questions/30600978/cpp-usr-bin-ld-cannot-find-lnameofthelibrary
