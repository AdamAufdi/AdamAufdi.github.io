---
layout: page
title: Robotics
description: Competitive robotics engineering, mechanical design, controls, and autonomous systems
img: assets/img/10.jpg
importance: 3
category: fun
---

## Technical Overview

This project documents the **engineering design, construction, and programming** of a competitive FTC robot developed during the 2022–2023 season. The work focused on achieving **high mechanical consistency, fast cycle times, and reliable autonomous performance** through iterative design, rigorous testing, and integrated sensing and control. I oversaw and personally designed nearly the entire mechanical system for this project.

Primary technical areas included:
- Custom mechanical mechanisms (intake, outtake, drivetrain)
- Sensor-driven autonomous navigation
- Advanced control algorithms
- Iterative design informed by competition performance

---

## Mechanical Architecture

The final robot architecture evolved through multiple major revisions, each addressing observed performance limitations.

Key mechanical systems included:
- **Horizontal scissor extension** (52” reach) enabling far high-pole scoring during autonomous
- **Pivoting vertical slides** paired with a versatile outtake basket
- **Retractable V-guide** for rapid and accurate pole alignment
- **Custom CNC-machined drivetrain** with low center of gravity
- **Custom deadwheel odometry pods** suspended on springs for durability and accuracy

Design choices prioritized rigidity, repeatability, and minimizing robot repositioning during scoring cycles.

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/10.jpg" title="Robot mechanical overview" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  Custom mechanical systems enabling fast, consistent scoring and autonomous reach.
</div>

---

## Intake and Outtake Systems

The **intake system** progressed through multiple claw designs to maximize grip reliability:
- Fully encircling cone geometry
- Large contact surface with compliant materials
- Wide opening for easier tele-operated alignment
- Slim profile for reliable transfer into the outtake

The **outtake system** was designed to tolerate positional and angular variation:
- Basket capable of accepting cones at up to ~80° misalignment
- Integrated limit switches for consistent retraction
- Weight-reduced structure with cutouts
- Added spring assistance to increase flip velocity
- Enclosed basket floor to prevent jamming

These systems allowed inconsistent cone pickups to be corrected mechanically rather than through driver compensation.

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/11.jpg" title="Intake and outtake mechanisms" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/12.jpg" title="Intake and outtake mechanisms" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  Intake and outtake designs emphasizing adaptability and mechanical forgiveness.
</div>

---

## Drivetrain and Odometry

The drivetrain was **custom CNC-machined** and designed for:
- High rigidity and repeatable motion
- Driving over ground junctions without loss of control
- Ample internal space for odometry integration

A **three-deadwheel odometry system** was used for localization:
- Spring-suspended deadwheels for terrain compliance
- Encoder-based position tracking
- High durability to withstand competition conditions

This base provided the most consistent motion platform the team had achieved to date.

---

## Control Systems and Programming

Robot control software emphasized **precision, repeatability, and concurrency**.

Driver control features:
- Cubic joystick scaling for fine low-speed control
- Fine-control mode for precision alignment
- Field-centric drive using IMU heading correction
- Automated cone cycling (“Autoglide”) coordinating subsystems during scoring

Autonomous systems included multiple preplanned routines (1+5, 1+7 variants) targeting different junctions and minimizing interference.

Key control algorithms:
- **PID control** for drivetrain and lift positioning
- **Finite State Machines** to sequence intake, transfer, extension, and scoring
- **Multithreading** to allow motion, localization, and mechanism control concurrently
- **Pose exponentials** for more accurate odometry integration than Euler methods

---

## Sensors and Localization

The robot used a heterogeneous sensor stack:
- 3 deadwheel encoders + IMU for odometry
- Logitech C270 webcam for AprilTag detection
- Distance sensor on claw for extension control in autonomous
- Color sensor for cone detection
- Limit switches for mechanism state detection
- Motor encoders for lift positioning
- **Intel T265 V-SLAM camera** for vision-based localization

Sensor fusion enabled reliable autonomous navigation and consistent scoring, even under variable field conditions.

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/13.jpg" title="Robot mechanical overview" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  vSLAM field map for localization.
</div>

---

## Iterative Design and Validation

Performance data from qualifiers directly informed redesigns:
- Transition from unstable four-bar mechanisms to slide-based extensions
- Addition of V-guide to improve alignment speed and accuracy
- Integration of distance and color sensors to improve autonomous reliability
- Mechanical aids (tip-cone bar) added where software solutions proved insufficient

At the state championship level, these refinements resulted in **high autonomous scoring consistency** and reliable cycle execution.

Below are pictures of an earlier design featuring a triple reverse four bar linkage, variable extension, and rotating turntable. This design was mechanically viable, but was proven not strategically viable for winning the game, and so the design was abandoned for the one featured previously.

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/15.jpg" title="Intake and outtake mechanisms" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/16.jpg" title="Intake and outtake mechanisms" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/17.jpg" title="Intake and outtake mechanisms" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  Earlier-season robot design.
</div>

---

## Technical Outcome

The final system demonstrated:
- High mechanical reliability under competition conditions
- Consistent autonomous performance using sensor-driven localization
- Rapid cycle times enabled by long reach and alignment aids
- Robust drivetrain and odometry foundation

This project served as a comprehensive application of **mechanical design, embedded control, sensor integration, and algorithmic autonomy** in a real-time competitive robotics environment. With this design, I led my team to the semi-finals at the world championship, and was ranked third in OPR (a statistic used in FIRST robotics to rank individual teams) in the world, and seventh in the all time hall of fame.

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/14.jpg" title="Robot mechanical overview" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
