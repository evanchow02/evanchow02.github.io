---
caption: #what displays in the portfolio grid:
  title: Autonomous Car Simulation
  subtitle: Spring 2023
  thumbnail: assets/img/portfolio/av_simulation/parked_cars.png
  
#what displays when the item is clicked:
title: Autonomous Car Simulation
subtitle: <b>Components:</b> Julia, Asynchronous Programming, Motion-Planning Algorithms, PID Controller
image: assets/img/portfolio/av_simulation/parked_cars_full.png #main image, can be a link or a file in assets/img/portfolio
alt: parked_cars

---
For the final project of my Autonomous Vehicles course, all students were paired up in teams to develop an autonomous vehicle for navigation in a simulated world. Using what we learned throughout the school semester about the components of an autonomous vehicle, our team split our software stack into three modules: localization, perception, and decision making. The localization module combines measurements received from a GPS and IMU to estimate the position of the ego vehicle and the perception module combines measurements received from two cameras to estimate the position of other vehicles on the road. An Extended Kalman Filter is used in both the localization and perception modules to pass accurate data to the decision making module, where vehicle control commands are computed and sent to the vehicle controller on the simulation server. A diagram of our complete autonomy stack is shown below.

<img src="assets/img/portfolio/av_simulation/av_stack_workflow.png" alt="autonomy_stack"/>

I was in charge of the decision making module and tasked with safely and properly navigating our vehicle between target passenger pick-up and drop-off zones on the map. To create proper autonomous navigation, I split the decision making module into two components: route planning and motion planning.

**Route Planning:** When first loading into the simulation server, the ego vehicle is placed in a random position on the map and given a target loading zone ID. Thus, before any commands (velocity, steering angle) can be sent to the ego vehicle, the decision making module is first tasked with determining the starting road segment of the ego vehicle and the path required to get to the target loading zone. The road segment corresponding to the current position of the ego vehicle is determined by comparing the position data from the localization module to each road segment in the map. The map generated in the server is represented through a dictionary where the key is a road segment ID number, and the value is a RoadSegment data type, which contains information about each individual road segment such as length, position, road segment type, and adjacent roads. With the boundaries of each road segment being defined with beginning and end points of the road, each road segment can be represented as a polygon. The entire map can then be traversed to determine which polygon or road segment the current position of the ego vehicle is in. To determine if the position of our ego vehicle is in a certain road segment polygon, I employ a ray casting algorithm between a line drawn through the point of interest and the edges of a polygon. 

Once the road segment position of the ego vehicle is established, I implemented Dijkstra’s algorithm to find the shortest travel distance path from the ego vehicle to the target loading zone ID. With the road segments and their respective neighbor roads being represented in the map dictionary with an adjacency list, Dijkstra’s algorithm reliably determines the sequence of road segment IDs creating the shortest path between the ego vehicle and the target loading zone. To ensure efficiency of route planning, I decided to implement Dijkstra’s algorithm with the heap data structure.

**Motion Planning:** Driving the ego vehicle involves calculating and sending a target velocity and steering angle to the car. To calculate the required target velocity of the vehicle for proper motion, a type of proportional controller is used, where the distance between the ego vehicle and another car or stop sign dictate the set target velocity. The closer the ego vehicle is to another car or stop sign, the lower the target velocity is set. The steering angle is also calculated using a proportional controller; however, to keep the ego vehicle within the lane boundaries of the road segment it is on, more computations first need to be done. Using a similar strategy as the solution to find which road segment the ego vehicle is on, each road segment can be split into a series of 3 polygons: one to represent the left side of the road, one to represent the right side of the road, and one to represent the middle of the road. The position of the ego vehicle can then be used to determine which side of a specific road segment the ego vehicle is on. After determining which side of the road the ego vehicle is on, the steering angle can be adjusted with the proportional controller to ensure the vehicle stays within the bounds of the road.

<video width="100%" controls> <source src="assets/img/portfolio/av_simulation/AV_video_project.mp4" type="video/mp4" alt="av_project"> </video>  

The final project code can be found here: [Complete AV Project](https://github.com/vikrammeyer/av-project)  
The decision making code can be found here: [Decision Making Module](https://github.com/vikrammeyer/av-project/blob/main/src/routing.jl)

{:.list-inline} 
- **Date:** Spring, 2023