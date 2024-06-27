# OpenCat

OpenCat is the open-source Arduino and Raspberry Pi-based quadruped robotic pet framework developed by Petoi, the maker of futuristic programmable robotic pets.

## Setup  Process:

To configure the board:

1. Download the repo and unfold. Remove the **-main** (or any branch name) suffix of the folder.

2. Open the file ftOpenCat.ino, select your robot and board version.
```cpp
// #define BITTLE  //Petoi 9 DOF robot dog: 1x on head + 8x on leg
// #define NYBBLE  //Petoi 11 DOF robot cat: 2x on head + 1x on tail + 8x on leg
#define ftBionicKit  //fischertechnik cat 8 DOF 8x on leg

// #define NyBoard_V0_1
// #define NyBoard_V0_2
// #define NyBoard_V1_0
// #define NyBoard_V1_1
// #define NyBoard_V1_2
#define FtArduinoUno
```

3. Comment out ```#define MAIN_SKETCH``` so that it will turn the code to the board configuration mode. Upload and follow the serial prompts to proceed.
```cpp
// #define MAIN_SKETCH
```

4. If you activate ```#define AUTO_INIT```, the program will automatically set up without prompts. It will not reset joint offsets but calibrate the IMU. It's just a convenient option for our production line.

5. Plug the USB uploader to the NyBoard and install the driver if no USB port is found under Arduino -> Tools -> Port.

6. Press the upload button (->) at the top-left corner in Arduino IDE.

7. Open the serial monitor of Arduino IDE. You can find the button either under Tools, or at the top-right corner of the IDE.

Set the serial monitor as **no line ending** and **115200** baud rate.
The serial prompts:
```
Reset joint offsets? (Y/n)
Y
```

Input ‘Y’ and hit enter, if you want to reset all the joint offsets to 0.

The program will do the reset, then update the constants and instinctive skills in the static memory.

8. IMU (Inertial Measurement Unit) calibration.

The serial prompts:
```
Calibrate the IMU? (Y/n):
Y
```
Input ‘Y’ and hit enter, if you have never calibrated the IMU or want to redo calibration.

Put the robot flat on the table and don't touch it. The robot will long beep six times to give you enough time. Then it will read hundreds of sensor data and save the offsets. It will beep when the calibration finishes.

When the serial monitor prints "Ready!", you can close the serial monitor to do the next step.

9. Uncomment ```#define MAIN_SKETCH``` to make it active. This time the code becomes the normal program for the major functionalities. Upload the code.
```cpp
#define MAIN_SKETCH
```
When the serial monitor prints "Ready!", the robot is ready to take your next instructions.

10. If you have never calibrated the joints’ offsets or reset the offsets in Step2, you need to calibrate them. If you boot up the robot with one side up, it will enter the calibration state automatically for you to install the legs. Otherwise, it will enter the normal rest state

11. You can use the serial monitor to calibrate it directly. Or you may plug in the Bluetooth dongle, and use the Petoi app (on Android/iOS) for a more user-friendly interface. The mobile app is available on:

* IOS: [App Store](https://apps.apple.com/us/app/petoi/id1581548095)
* Android: [Google Play](https://play.google.com/store/apps/details?id=com.petoi.petoiapp)

You can refer to the calibration section in the user manual (https://bittle.petoi.com/6-calibration) and Guide for the Petoi App(https://docs.petoi.com/app-guide).

## Resources:
* [STEM Curriculum & Educational Robots for Teaching Coding Robotics](https://www.petoi.com/pages/resources-curriculum-stem-coding-robot)
* [Advanced tutorials made by users](https://www.youtube.com/playlist?list=PLHMFXft_rV6MWNGyofDzRhpatxZuUZMdg)
* [Review, open-box, and demos by users](https://www.youtube.com/playlist?list=PLHMFXft_rV6PSS3Qu5yQ-0iPW-ohu1sM3)
* [OpenCat robot showcase by users](https://www.petoi.com/pages/petoi-open-source-extensions-user-demos-and-hacks)
* [OpenCat robot gallery](https://www.petoi.com/pages/robot-pet-gallery)

The [old repository for OpenCat](https://github.com/PetoiCamp/OpenCat-Old) is too redundant with large image logs and is obsolete without further updates.
