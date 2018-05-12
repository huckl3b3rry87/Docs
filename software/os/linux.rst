Linux
=====


Useful Programs
------------------
In the terminal:
::

  sudo dpkg --install atom-amd64.deb
  sudo apt install ffmpeg
  sudo apt-get install cmake bar time binutils make libssl-dev gfortran libunwind8-dev gcc g++ #clang curl perl wget m4 patch pkg-config
  sudo apt-get install gsfonts-x11
  sudo apt-get install notepadqq
  sudo apt-get update
  sudo apt-get install gfortran
  sudo apt-get install libnlopt0
  sudo apt-get install openssh-server
  sudo apt install ipmiutil
  sudo apt-get install hdf5-tools
  apm install latex # Atom package manager for latex!
  sudo apt-get install pdf2svg # for PGFPlots
  pip install sphinxcontrib-bibtex
  sudo apt-get install texlive-luatex
  sudo apt install aptitude
  sudo apt-get install freecad
  sudo apt install blender
  sudo apt install rpm
  apm install latex
  sudo apt autoremove


Basic Linux Commands
--------------------

Never run an executable in root!

Some more info can be found on ` this page <https://www.cyberciti.biz/faq/tar-extract-linux/>`.

To move a folder an all of its contents:
::
  mv /path/sourcefolder/* /path/destinationfolder/

To unpack a tar file:
::

  tar -xvf file.tar

To extract a .tar.gz:
::

  tar -xzvf file.tar.gz

.. note:: Modern ``tar`` can recognize the format automatically:
::

  sudo tar xf armadillo-8.300.3.tar.xz -C /opt


Unzip:
::

  unzip stuff.zip -d /destination/folder

directory comment:
::

  $HOME = /home/febbo

Run a jar file:
java -jar lad


Useful Tools
-----------------------------------

* Synaptic Package Manager


/etc/bash.bashrc  vs. $HOME/.bashrc
--------------------------------------

Be careful there are two files that configure the terminal!

http://unix.stackexchange.com/questions/140207/messed-up-bash-bashrc-file-commands-not-working-anymore

in my ``$HOME/.bashrc``:
::

  alias blender='/opt/blender/blender'
  alias julia='/opt/julia-6445c82d00/bin/julia'
  alias docs='sphinx-autobuild . _build_html'
  export DYLD_LIBRARY_PATH="$HOME/knitro/lib:$DYLD_LIBRARY_PATH"
  export LD_LIBRARY_PATH="$HOME/knitro/lib:$LD_LIBRARY_PATH"
  export PYTHONPATH=$PYTHONPATH:/usr/lib/python2.7/dist-packages
  export GAZEBO_PLUGIN_PATH=/home/febbo/.julia/v0.5/OCP/MAVs/workspace/src/velodyne_plugin/build/:${GAZEBO_PLUGIN_PATH}
  source /opt/ros/kinetic/setup.bash
  export ROS_PACKAGE_PATH=/home/febbo/.julia/v0.5/OCP/MAVs/workspace:$ROS_PACKAGE_PATH


Ubuntu package manager
------------------------

https://launchpad.net/ubuntu/+source/matplotlib

Video Stuff
----------------

to converte to MP4
^^^^^^^^^^^^^^^^^^^^^
Type:
::

  ffmpeg -f gif -i mainSimPath.gif RESULT.mp4

Quickly convert to ``.gif`` files:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Following `this link <https://superuser.com/questions/556029/how-do-i-convert-a-video-to-gif-using-ffmpeg-with-reasonable-quality>`_

Add this to your ``~/bash_profile`` file:
::

  # Convert video to gif file.
  # Usage: video2gif video_file (scale) (fps)
  video2gif() {
    ffmpeg -y -i "${1}" -vf fps=${3:-30},scale=${2:-320}:-1:flags=lanczos,palettegen "${1}.png"
    ffmpeg -i "${1}" -i "${1}.png" -filter_complex "fps=${3:-10},scale=${2:-320}:-1:flags=lanczos[x];[x][1:v]paletteuse" "${1}".gif
    rm "${1}.png"
  }

Then load it in the ``.bashrc`` file:
::

  . ~/.bash_profile
