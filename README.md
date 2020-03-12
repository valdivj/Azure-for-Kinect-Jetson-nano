# Azure-for-Kinect-Jetson-nano
Instructions to Run Azure For Kinect on Jetson Nano

Here are the Instructions to get the Azure for Kinect to run on the Jetson nano.

This is at the very early stages of devlopment so things will probably change later on.

https://github.com/microsoft/Azure-Kinect-Sensor-SDK Good place to start for  answers.

I started with a fresh image on the Jetson Nano


1. Plug Kinect into Nano

2. $sudo apt-get install libglu1-mesa-dev freeglut3-dev mesa-common-dev

3. $sudo apt-get install openssl

4. $sudo apt-get install -y ninja-build

5. $sudo apt-get install libssl-dev

6. $sudo apt install libsoundio-dev

7. $sudo apt-get install libxinerama-dev

8. $sudo apt-get install libsdl2-dev

9. download package :https://www.nuget.org/api/v2/package/Microsoft.Azure.Kinect.Sensor/1.4.0-alpha.4

You will need to pull this file ”libdepthengine.so.2.0” located at “/linux/lib/native/arm64/release/”

from the package you down loaded. You can either use “Archive Manger” to get it or change the “.nupkg” to “.tar” and unzip it

Once you find  “/linux/lib/native/arm64/release/libdepthengine.so.2.0” drag it into this location “/lib/aarch64-linux-gnu/"

$sudo chmod a+rwx /lib/aarch64-linux-gnu    Will Give permmision to drag ”libdepthengine.so.2.0” into file.

10. $git clone https://github.com/microsoft/Azure-Kinect-Sensor-SDK.git

I had some issues with this it kept asking for password 

So I just went to :https://github.com/microsoft/Azure-Kinect-Sensor-SDK

and just use the “Clone or Download button” to get it

11.$cd Azure-Kinect-Sensor-SDK

12. $mkdir build && cd build

13. $cmake .. -GNinja

14. $ninja

15. Copy 'scripts/99-k4a.rules' from “/home/nano/Azure-Kinect-Sensor-SDK/scripts 

to '/etc/udev/rules.d/' you may need this:$sudo chmod a+rwx  /etc/udev/rules.d  for filr permmision.

16.You should still be in the build folder $~/Azure-Kinect-Sensor_SDK/build$./bin/k4aviewer

Will start the viewer. If the Viewer dosent reconize Kinect close Viewer and unplug and plug back in to  Kinect 

and restart Viewer.










