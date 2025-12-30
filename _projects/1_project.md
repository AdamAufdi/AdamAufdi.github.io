---
layout: page
title: Komatsu SDV
description: Software Defined Vehicle and modular sensor testbed for perception and autonomy
img: assets/img/6.jpg
importance: 1
category: work
related_publications: false
---

## Project Overview

This project is a modular **Software Defined Vehicle (SDV)** developed for Komatsu’s Automation Center of Excellence (ACoE) as part of the *Tanki III DUPLO Project*.  
The goal was to create a **reconfigurable, sensor-rich testbed** that could support a wide range of automation R&D efforts, including hardware validation, perception development, data collection, and early-stage autonomy prototyping.

The platform is built on a drill automation mockup and intentionally designed to mirror real SDV constraints: distributed compute, heterogeneous sensors, nontrivial power systems, and field-deployable robustness. Rather than a one-off prototype, Tanki III was designed as a **repeatable architecture** that could evolve alongside future projects.

Role:  
**Adam Aufderheide** – End-to-end design, layout, and implementation of the mechanical and electrical systems, including sensor mounting, power distribution, compute integration, and custom PCB design.

Status: **Complete**, demonstrated under self-powered operation with active sensors and compute.

---

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    <!-- Slide 4: Before/After Tanki III DUPLO mockup -->
    {% include figure.liquid path="assets/img/1.jpg" title="Mockup before and after integration" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  Tanki III DUPLO platform before and after sensor, compute, and communication system integration.
</div>

---

## Mechanical & Sensor Integration

The mechanical system was designed around three primary constraints:

1. **Sensor field-of-view optimization** (front and rear coverage)  
2. **Environmental durability** (weather exposure, vibration, thermal effects)  
3. **Modularity** (rapid addition, removal, or relocation of hardware)

The external sensor suite includes:
- 2× Continental ARS548 radar units  
- 2× Ouster OS0-128 lidar sensors  
- 6× GMSL cameras  
- Self-cleaning camera system  
- Dual GNSS antennas (Leica CGA100)  
- Radio and communication antennas  
- Reserved space for Starlink Mini and additional radar/lidar units

Mounting solutions were selected based on functional requirements rather than uniformity.  
High-heat or precision-critical components (notably the lidar units) were mounted using **1/16” bent steel sheet metal** to increase thermal conductivity and prevent deformation. Other components were mounted using **3D-printed fixtures**, enabling fast iteration at low cost.

This approach allowed the platform to remain mechanically stable while still supporting ongoing experimental changes.

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    <!-- Slide 5: Mechanical overview with labeled sensors -->
    {% include figure.liquid path="assets/img/2.jpg" title="Mechanical overview and external sensors" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  External sensor layout showing radar, lidar, cameras, GNSS, and communications hardware.
</div>

---

## Electrical Architecture

The electrical system was designed to support **automotive-scale power demands** while remaining serviceable and safe for development use.

Key internal components include:
- Intel NUC (S76 Meercat)
- 2× NVIDIA Jetson compute modules
- POE switch
- Dual Ethernet switches
- Rajant Cardinal radio box
- Leica GNSS receiver
- Honeywell IMU
- DC–DC converters for 12V and 24V rails

The platform operates from a **48V battery system**, stepped down into:
- Two independent 12V systems
- One 24V system

Total system power draw is approximately **680 W**, with peak current approaching **50 A**, necessitating careful power budgeting and cable management.  
An **emergency stop (E-stop)** was incorporated as a mandatory safety feature, reflecting real-world industrial requirements.

The electrical cabinet layout prioritized airflow, accessibility, and clear separation between compute, networking, and power conversion components.

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    <!-- Slide 11: Electrical cabinet / internal components -->
    {% include figure.liquid path="assets/img/3.jpg" title="Internal electrical cabinet layout" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  Internal electrical layout showing compute, networking, and power distribution hardware.
</div>

---

## Software Defined Vehicle Architecture

Tanki III was intentionally structured as a **Software Defined Vehicle**, with clear separation between hardware capability and software behavior.

The system architecture is divided into:
- **Perception**: camera, lidar, and radar sensor stack  
- **Compute**: NVIDIA Jetson modules and Intel NUC  
- **Motion**: motor controller and closed-loop control  
- **Networking**: multi-switch architecture enabling isolated and shared networks  

This modular approach allows individual subsystems to be upgraded or reconfigured without redesigning the entire platform, making Tanki III suitable for a wide range of autonomy experiments.

<div class="row justify-content-sm-center">
  <div class="col-sm-8 mt-3 mt-md-0">
    <!-- Slide 14: Tanki III SDV overview -->
    {% include figure.liquid path="assets/img/4.jpg" title="Software Defined Vehicle architecture" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  High-level SDV architecture showing perception, compute, motion, and networking layers.
</div>

---

## Sensors, Control, and Validation

All sensors and control systems are integrated using **ROS 2**, enabling standardized data flow and rapid prototyping.

Key elements include:
- GMSL camera pipelines with ROS 2 nodes and image topics
- Ouster lidar and Continental radar drivers publishing PointCloud2 data
- Perception subscribers consuming raw and post-processed sensor data
- Motor controller supporting closed-loop PID control with encoder feedback

This architecture allowed for clear separation between **current implementations** and **future expansion**, ensuring that the platform remains useful as perception and autonomy stacks mature.

---

## Motor Controller PCB Design

To support reliable motion control and clean system integration, a **custom motor controller PCB** was designed and implemented.

The PCB provides:
- DB-25 interface to the Roboteq GBLB2660TE motor controller  
- Dual encoder inputs for motor feedback  
- CAN bus connectivity for signal communication  
- RC receiver interface for tele-operated control  

By consolidating these interfaces onto a single board, wiring complexity was significantly reduced and system reliability improved. Designing and validating this PCB required translating high-level control requirements into a physically robust, electrically sound solution—representing one of the most technically demanding aspects of the project.

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    <!-- Slide 20: Motor controller PCB -->
    {% include figure.liquid path="assets/img/5.jpg" title="Custom motor controller PCB" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  Custom PCB enabling motor control, encoder feedback, CAN communication, and RC teleoperation.
</div>

---

## Outcome

The modular test bed project resulted in a **fully operational Software Defined Vehicle testbed** capable of supporting real-world autonomy research.  
It successfully integrated mechanical design, electrical systems, embedded compute, and software architecture into a single cohesive platform, providing Komatsu’s Automation R&D teams with a flexible foundation for future development.
