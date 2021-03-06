Build Tools
************


`catkin <http://wiki.ros.org/catkin#Installing_catkin>`_
=============================================================

This is the official build system of ROS, it uses the CMake macros and Python to add functionality to Cmake.

`Installation Instructions <http://wiki.ros.org/catkin#Installing_catkin>`_

catkin-tools
-------------
These tools are used to facilitate a merged build process. That is several inter-dependent but separately developed CMake projects

`Installation <http://catkin-tools.readthedocs.io/en/latest/installing.html>`_:
::

  sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu `lsb_release -sc` main" > /etc/apt/sources.list.d/ros-latest.list'
  wget http://packages.ros.org/ros.key -O - | sudo apt-key add -
  sudo apt-get update
  sudo apt-get install python-catkin-tools

.. warning::

  If you this was built on an old machine or paths got updated (e.g. a new version of julia) then it may be necessary to clean out the build:

to clean out an old build:
::
    rm -rf build


If you move a package, delete the ``build`` and the ``devel`` folders then do a ``catkin_make``


`CMake <https://cmake.org/>`_
=================================

`Ninja <https://ninja-build.org/>`_
=======================================
a small build system:
::

  sudo apt-get install ninja-build


`Linuxbrew <http://linuxbrew.sh/>`_
=========================================
For working with Linux and Mac
install:
::

  sudo apt install linuxbrew-wrapper

then:
::

   brew install libyaml
