# Automatic-Emergency-Braking-System-for-ROS2-based-Race-Cars-using-iTTC
This repository focuses on the development and implementation of an Automatic Emergency Braking (AEB) system for race cars. The primary intent is to bolster safety measures by ensuring cars traveling at high velocities can prevent imminent collisions. 


## Overview

In the Automatic Emergency Braking System project, I delved deep into the realm of safety-critical systems, specifically targeting the prevention of high-speed vehicular collisions. Using ROS 2 and its associated messaging protocols, I conceptualized and executed an autonomous braking mechanism for a simulated race car, grounded in the principles of Instantaneous Time to Collision (iTTC).

![image](https://github.com/Saibernard/Autonomous-Race-Cars-Automatic-Emergency-Braking-System-ROS2-based--using-iTTC/assets/112599512/87e1f661-19e8-43c5-b638-fdbee589059f)


## Key Components and Features

- **Deep Dive into LaserScan Message:** The foundational component of this project revolved around the LaserScan message. My focus was particularly drawn towards the `ranges` field, which constituted an array of range measurements. Arranged radially based on LiDAR readings, these measurements became instrumental in driving the iTTC calculations.

- **Leveraging the Odometry Message:** By intricately exploring the Odometry message, I sourced key insights related to the car's dynamics - its position, orientation, and velocity. Such data points, when interfaced with the LaserScan readings, were pivotal in enhancing the accuracy of the iTTC computation.

- **iTTC Calculation Mechanism:** The iTTC, which denotes the time required for a car to collide with an obstacle based on its current trajectory and speed, was calculated via:

iTTC = r / (-r_dot)


In this formula, `r` stands for the instantaneous range measurements extracted from the LaserScan message, whereas `r_dot` represents the current range rate. The subsequent array of iTTCs, corresponding to each LiDAR angle, served as an alert system, signaling potential collisions when readings went below specific thresholds.

- **Design of the Automatic Emergency Braking Node:** One of the project's cornerstones was the creation of a dedicated ROS 2 node. This node was set up to subscribe to both LaserScan and Odometry messages, analyzing real-time LaserScan data. Should a potential collision be detected, the node would then initiate an automatic brake by publishing an AckermannDriveStamped message, setting the speed field to 0.0 m/s.

- **Simulation and Real-world Testing:** To validate the efficacy of the braking system, I incorporated the `kb_teleop` parameter in `sim.yaml`. This allowed for keyboard-driven control of the simulated car. Throughout the simulation, I meticulously navigated the car through a variety of scenarios, such as driving through hallways and heading directly towards walls. These tests confirmed the system's robustness, with the car halting exclusively when a collision was imminent, and otherwise navigating seamlessly.

![image](https://github.com/Saibernard/Autonomous-Race-Cars-Automatic-Emergency-Braking-System-ROS2-based--using-iTTC/assets/112599512/eca2b418-83e9-48a0-9fcc-8c57b767f27f)

![image](https://github.com/Saibernard/Autonomous-Race-Cars-Automatic-Emergency-Braking-System-ROS2-based--using-iTTC/assets/112599512/0965152c-2ea8-4a64-998d-32bad469a590)

## Technologies and Tools

- **ROS 2:** As the backbone of the project, ROS 2 facilitated messaging, node creation, and overall system integration.
- **LiDAR:** This was crucial in obtaining radial distance measurements for the iTTC calculations.
- **C++/Python:** The system's logic and functionality were scripted using one of these programming languages.

This project stands as a testament to the intricate melding of robotics, software engineering, and safety protocols. Through rigorous coding, testing, and simulation, I was able to actualize a reliable safety system that promises to drastically reduce high-speed vehicular collisions. All the code, simulation results, and further documentation can be accessed on this repository.

