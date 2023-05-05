---
caption: #what displays in the portfolio grid:
  title: Inverse Kinematic Robotic Arm
  subtitle: Spring 2023
  thumbnail: assets/img/portfolio/robotic_arm/arm_bolt.jpg
  
#what displays when the item is clicked:
title: Inverse Kinematic Robotic Arm
subtitle: <b>Components:</b> C++, Inverse Kinematics, CAD, 3D-Printing, Laser Cutting, Soldering 
image: assets/img/portfolio/robotic_arm/arm_bolt.jpg #main image, can be a link or a file in assets/img/portfolio
alt: robotic_arm

---
Depicted above is the 5 degree of freedom robotic arm I designed and built. An electromagnet serves as the end effector and the motion of the robotic arm is dictated by 3 linear potentiometers, where each potentiometer represents the electromagnet's three-dimensional Cartesian coordinates. Inverse kinematics is used to determine the joint angles to achieve specified spatial coordinates. Additionally, rotary potentiometers and switches are used to adjust the orientation of the electromagnet and turn the robotic arm and electromagnet on and off, respectively. The complete arm is stored in a self-designed box to create a clean user interface and protect the electrical components and user from each other.

The construction of the inverse kinematic arm can be split into three categories: hardware, electrical, and software.

<video width="100%" autoplay loop controls muted> <source src="assets/img/portfolio/robotic_arm/arm_explode_collapse.mp4" type="video/mp4"> </video>  

**Hardware:** The main body of the robotic arm was designed using CAD and 3D printing. The links of the arm are attached and actuated with 180ᵒ servos to allow for 5 degrees of freedom. A total of 6 servos are used to actuate the arm with all servos being controlled by a servo shield attached to an Arduino Uno.

<img src="assets/img/portfolio/robotic_arm/robotic_arm_cad.png" alt="robotic_arm_cad"/>

To operate the arm, 5 potentiometers (3 linear, 2 rotary) and 2 switches are used. The three linear potentiometers control the x, y, and z Cartesian coordinates of the end effector and the 2 rotary potentiometers control the rotation (roll, pitch) of the end effector. 2 switches are used to turn the robotic arm and electromagnet arm on and off, respectively.

<img src="assets/img/portfolio/robotic_arm/controls.jpg" alt="controls"/>

**Electrical:** The 4 larger servos on the arm operate at 5 volts and 3 amperes, the 2 micro-servos operate at 5 volts and 1 ampere, and the electromagnet operates at 5 volts and < 1 ampere . Thus, to accommodate such power requirements, a 5V and 15A power supply was chosen. The power supply powers the servo shield using a barrel jack adaptor with screw terminals while the Arduino Uno is powered by a laptop. The servos plug directly into the servo pins on the servo shield and are controlled with PWM on an I2C communication protocol. The potentiometers plug into the analog pins on the servo shield and the switches plug into the digital pins on the servo shield.

<img src="assets/img/portfolio/robotic_arm/complete_wiring.jpg" alt="wiring"/>

**Software:** All software was developed using the Arduino C++ variant language with the Adafruit PWM Servo Driver library. The inverse kinematic math used to determine joint angles required the implementation of the law of cosines in helper functions, while the functions used to drive the servo motors were provided by the Adafruit library. The Adafruit driver library controls servos by specifying the start and end time of a PWM output within a 4096-part cycle. However, to make the inverse kinematic algorithm clearer, a helper function was made that converts an angle in degrees to the appropriate input value for the Adafruit library driver function.

While the implementation of inverse kinematics in code didn’t require much more than utilizing the law of cosines, figuring out the bounds of the end effector's position proved to be the challenge. To determine the allowable x, y, and z values of the robotic arm, the length of the arm's links and the restricted range of motion of the servos (180ᵒ) all needed to be considered, increasing the complexity of the inverse kinematic solutions. Ultimately, I used an iterative approach in Excel to figure out the bounds of the robotic arm’s motion.

<video width="100%" controls> <source src="assets/img/portfolio/robotic_arm/robotic_arm_video.mp4" type="video/mp4" alt="robot_arm_video"> </video>

The project code can be found here: [Complete Robotic Arm Project](https://github.com/evanchow02/inverse_kinematic_robotic_arm)  

{:.list-inline} 
- **Date:** Spring, 2023