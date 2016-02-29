-----------------------
YouBot.APK Installation
-----------------------
The common way to install an APK file (Android Package) is to use app installer that can be acquired in Android Market.
	- Go to Android Market
	- Download and install an app installer
	- Copy YouBot.APK to SD card
	- Run app installer. App installer will detect all APK file in SD card.
	- Install YouBot.APK


-----------------------
youBotAndroid Installation
-----------------------

You must have the KUKA youBot API installed. Further instructions to install the API can be found on http://www.youbot-store.com

If not already done, download or checkout the demo sources into a catkin folder.
Assuming that you created such a catkin folder at ~/catkin_ws, this can be done e.g. via

$ cd ~/catkin_ws/src
$ git clone http://github.com/wnowak/youbot_applications

In order to compile the demo, enter

$ cd ~/catkin_ws
$ catkin_make

You can then run the program using

$ sudo devel/lib/youbot_android/youbot_android

-----------------------
Running YouBot App
-----------------------
After YouBot.APK and youBotAndroid are installed, KUKA youBot can now be controlled from youBot App.
It is suggested that the KUKA youBot PC are already paired as bluetooth device with Android mobile device before running YouBot App.
	- Run youbot_android on KUKA youBot PC using
	- Run YouBot App on Android mobile device
	- Click "Select Device" from main menu
	- Select KUKA youBot PC. After selecting the device, YouBot app will return automatically to the main menu
	- Select controller mode (DRIVE mode or SHIFT mode)
	- Once the controller selected, YouBot App will automatically try to connect with the socket opened by youbot_android on PC.
	- Control KUKA youBot.
