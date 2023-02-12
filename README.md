# Object-Chasing-2-Wheeled-Robot-in-ROS-and-Simulation-in-Gazebo-Environment
This project involves designing and building a mobile robot that is capable of chasing and following white colored balls and to  detect and chase the ball, this bot employed a camera to capture frames and do image processing using open cv.The ball's characteristics, such as color, shape, and size, can be employed. goal was to create a rudimentary prototype for a bot that can detect and follow color.

The ROS project consists of 2 packages, my_robot and ball_chaser. The my_robot package contains the robot and world models which can be visualised in the Gazebo simulator when the package is run using the roslaunch command. The ball_chaser package is responsible for detecting and moving towards any white object in front of the robot by reading the feed from the camera attached to the front of the robot.

### Objective
- Design and Construct a 2 Wheeled Mobile Robot Which Detect and Chase The Specific Colour Ball
- We Implement This Robot in Robotic Operating System (ROS) and Simulation in Gazebo Environment

### Software Used
- Ros Noestic
- Gazebo

## Structure of the Robot  
**There are two packages within this repository:**
> **1. my_robot**
This package defines the mobile robot under URDF as well the world that it is housed within.  
> **2. ball_chaser**
This package contains two nodes which are responsible for locating the position of the white ball in the camera field of view and then sending the corresponding commands to the mobile robot to follow the white ball.

<h3><center>IMPLEMENTATION</center></h3>  
<h3>WORKING PRINCIPLE:</h3>

- The camera fixed on top of the robot captures the image.
- Then the image is processed and converted into pixel data.
- Then it search for white colour with pixel value as “255”.
- If the spherical white colour is detected, Then the robot starts following it
- If the ball presents in the right side of the robot then the robot move in right side with angular velocity “-1” until it is straight with the robot
- If the ball is present in the left side of the robot then the robot moves in left side with the angular velocity “1” until it is straight to the robot
- When ball is straight to the robot then angular velocity is 0
- If the white pixel is detected, the robot assumes it to be the ball and it starts following it.
- But if the pixels are not detected, it captures the image until it detects a white pixel.
- This description of the robot motion will be in the script files

<h3>Script Files</h3> 
We created 2 scripts files, the first one is process_image.cpp helps us to process the image and gives the direction,velocity and angular velocity for the robot, which act as subscriber it subscribes the image from the gazebo and process it, determines whether the ball is present or not. Based on the placement of the ball it assigns the linear and angular values for the variables in the srv file (DriveToTarget.srv). (User defined service file) and drive_bot.cpp act as publisher and it publishes the linear velocity and angular velocity for the robot in gazebo
<br>
<br>
<h4>Service file</h4>  

- DriveToTarget.srv  

<h4>Script Files</h4>  

- process_image.cpp  
- drive_bot.cpp  

<h4>Launch File</h4>  

- world.launch  
- robot_description.launch
- ball_chaser.launch


> ## Commands To Run the Simulations:
`$ roslaunch my_robot world.launch`  
`$ roslaunch ball_chaser ball_chaser.launch`  
**World File Simulation:**
<br>
![image](https://user-images.githubusercontent.com/120790343/218313841-d4651cea-e72e-4b8c-a5ac-6332f1d5676f.png)
<br>
<br>
**Image of Robot:**
<br>
![image](https://user-images.githubusercontent.com/120790343/218313858-e82a39c4-1a09-41ff-b706-026b7fd96252.png)
<br>
<br>
**RQT GRAPH**
<br>
![image](https://user-images.githubusercontent.com/120790343/218313917-bfc5ff37-4fb0-4ab8-8856-abea04fbe529.png)
<br>
<br>
### Conclusion
Finally the Robot detected the white ball and tracked it, The velocity results of linear and angular along all axes i.e., X, Y, Z showed in the terminal, and if the white coloured ball is kept in camera view of the robot, then the robot detect it and start chasing it, Hence the robot working perfectly.
