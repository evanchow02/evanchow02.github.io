---
caption: #what displays in the portfolio grid:
  title: Haptic Thermal Feedback Array
  subtitle: Summer 2022
  thumbnail: assets/img/portfolio/haptic_thermal/thermal_feedback_thumbnail.jpg
  
#what displays when the item is clicked:
title: Haptic Thermal Feedback Array
subtitle: <b>Components:</b> C++, Python, Unity, Thermal Imaging, CAD, 3D-Printing, Soldering
image: assets/img/portfolio/haptic_thermal/thermal_feedback_thumbnail.jpg #main image, can be a link or a file in assets/img/portfolio
alt: thermal_feedback

---
During Summer 2022, I was hired as an undergraduate researcher at the Vanderbilt [Robotics and Autonomous Systems Lab](https://lab.vanderbilt.edu/rasl/). Over the 3 months of the internship, I worked on further developing and prototyping a haptic thermal system that would be capable of bringing thermal sensation to augmented reality. 

Within the first week of summer research, I read prior research and documentation on similar systems to become familiar with the science and hardware required to build such a system. With a single heat delivery device known as a thermal electric module (TEM) already created by the lab as a proof of concept, I spent the next 3 weeks crimping, soldering, 3D modeling, 3D printing, and assembling hardware to scale the single proof of concept TEM to a 3x3 array of TEM devices. In addition to prototyping a larger heat delivery system, I programmed the system's control code, which handled heat delivery to specified input temperatures. By the end of the first month of my internship, a complete yet unreliable thermal system was created with capabilities of delivering heating or cooling to maintain TEM surface temperatures between -20 degrees Celsius and 100 degrees Celsius. 

<img src="assets/img/portfolio/haptic_thermal/3x3_array.jpg" alt="3x3_array" width="700"/>
While the initial 3x3 array prototype allowed for better thermal detection and testing, the fragile circuitry on the bread board led to sporadic issues such as command signal delays that caused multiple TEM devices to overheat and melt. Because of such faults and concerns for the user's safety, for the next month a graduate student and I started working on transitioning the thermal device to a 4x4 array controlled by a PCB. Safety hardware such as emergency shut off switches and software fail safes were also implemented. After weeks of redesigning mounts, building TEM devices, assembling hardware, and updating the control code to provide more thermal device features, a more robust 4x4 thermal array was developed.

<img src="assets/img/portfolio/haptic_thermal/pcb_device_version.jpg" alt="pcb_thermal_device" width="700"/>
<img src="assets/img/portfolio/haptic_thermal/pcb_device_closeup.jpg" alt="pcb_thermal_device" width="700"/>

The video below, produced from a thermal camera, shows the temperature performance of the thermal array in degrees Celcius.
<video width="700" autoplay controls muted> <source src="assets/img/portfolio/haptic_thermal/thermal_cam_video.mp4" type="video/mp4"> </video>
  
The last month of my summer research consisted of implementing the 4x4 thermal array with augmented reality. Using Unity, I developed 3 GUIs to test different capabilities of the thermal system. In the first GUI, a specified temperature is delivered to a single black or green region specified by the user.

<img src="assets/img/portfolio/haptic_thermal/region_gui.jpg" alt="gui_1" width="700"/>
In the second GUI, the user is able to select anywhere on the 4x4 graphic, which is used to depict the individual thermal devices in the system. Wherever the user selects, a specified temperature will be concentrated at that point and radiate outwards. This allows the user to click and drag their mouse around the graphic and feel thermal sensations tracing the same path on their physical hand.

<img src="assets/img/portfolio/haptic_thermal/proximity_gui.jpg" alt="gui_2" width="700"/>
In the third GUI, the user utilizes a HoloLens2 to track their hand. When the user's hand comes into contact with the white box, a red ball moves across the screen, indicating where a specified temperature is applied. If the user's hand ever leaves the white box, the thermal system will shut off; however, if the user's hand remains in contact with the white box as the red ball moves over it, then they will experience a thermal sensation across their hand.

<img src="assets/img/portfolio/haptic_thermal/rolling_ball_gui.jpg" alt="gui_3" width="700"/>
During my three months of summer research, I was able to learn much about control systems and gained many valuable skills with hardware assembly and firmware. However, perhaps one of the most valuable skills I learned was how to problem solve, but in a way different than homework problem sets or class assignments. Above comments on the highlights of my summer research, and while I am proud of all that I was able to create and learn during my experience, a majority of the three months were filled with rebuilding broken hardware, debugging code, and troubleshooting with a multimeter and logic analyzer. Initially when problems would arise, I would often have to ask a graduate student on what they thought went wrong. How they methodically dissected the issue to find the root cause of the problem was practical problem solving that I was unfamiliar with but eager to learn. How they asked me continuously narrowing questions to lead their investigation drew similarities from the way a medical doctor diagnoses a patient, and often succeeded. With practice and more observation, I was eventually able to troubleshoot some issues on my own. I thoroughly enjoyed this experience and look forward to pursuing future opportunities to continue learning and growing my skillset.

<img src="assets/img/portfolio/haptic_thermal/hololens.jpg" alt="hololens_selfie" width="400"/>




{:.list-inline} 
- **Date:** Summer, 2022