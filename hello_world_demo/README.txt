Hello World Demo Application
----------------------------

The hello_world_demo is an example application to show you how to use the 
KUKA youBot API for writing your own applications. You can use all the sources 
in this directory as a template. Controlling both, the KUKA youBot base and 
the youBot manipulator are shown in this example.

The program will start, moving the base and the arm. The youBot will move
approx. 10cm forwards, then approx. 10cm backwards, then approx. 10cm to the
left and approx. 10cm to the right. Afterwards it will ”unfold” the arm and
”fold” it again.

If you want to write your own application you can use this sources and folder
structure as a template.


Installation
------------

We assume, that you have installed the KUKA youBot API already. Further
instructions to install the API can be found on http://www.youbot-store.com

If not already done, download or checkout the demo sources into a catkin
folder. Assuming that you created such a catkin folder at ~/catkin_ws, this can be
done e.g. via

$ cd ~/catkin_ws/src
$ git clone http://github.com/wnowak/youbot_applications

In order to compile the demo, enter

$ cd ~/catkin_ws
$ catkin_make

During compilation a window should appear to enter your password. This is
needed to give the required access rights to the generated binary in order to run
the EtherCAT master. Alternatively the setcap command used here can be also run
manually after compilation finished.


Usage
-----

To start the application use:

$ rosrun hello_world_demo youBot_HelloWorldDemo 



License
-------

This software is published under a dual-license: GNU Lesser General Public
License LGPL 2.1 and BSD license. The dual-license implies that users of this
code may choose which terms they prefer.


Support
-------

Mail to users@youbot-community.org  
or go to http://lists.youbot-community.org/mailman/listinfo/users to 
subscribe to the mailing list
