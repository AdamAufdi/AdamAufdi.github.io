---
layout: page
title: Automated Visual Navigation Testing Pipeline
description: MATLAB–Python–Blender pipeline for rendering, data association, and evaluation of visual navigation algorithms
img: assets/img/7.jpg
importance: 2
category: work
#giscus_comments: true
---

## Project Overview

This project developed an **automated testing pipeline for visual navigation algorithms**, designed to evaluate robustness against the non-linear, non-Gaussian errors introduced during **data association**. The work was conducted in the **Sensing, Controls, and Probabilistic Estimation (SCOPE) Lab** and targeted navigation scenarios where real imagery of the environment is unavailable or impractical to collect, such as extraterrestrial terrain.

The pipeline integrates **MATLAB, Python, and Blender** into a single automated workflow. MATLAB drives the navigation and estimation algorithms, Blender generates physically realistic rendered imagery from specified camera poses, and Python performs feature detection and data association. The system extends existing MATLAB-based visual navigation tools by enabling large-scale, repeatable testing using rendered image data.

Role:  
**Adam Aufderheide** – Pipeline architecture design, MATLAB–Python–Blender integration, automation, and system validation.

Status: **Complete**, demonstrated under and reliable when tested across various data sets.
---

## Visual Navigation and Data Association

Visual navigation algorithms estimate a camera’s **pose (position and orientation)** from images of the surrounding environment. A typical processing pipeline includes:

1. Capturing an image of the environment  
2. Detecting visual features (e.g., ORB, SIFT, SURF)  
3. **Associating detected features** with a known map or database  
4. Feeding labeled feature coordinates into a navigation estimator  

Step 3—**data association**—is a critical failure point. Classical estimators such as the Extended Kalman Filter often assume perfect association, an assumption that can lead to estimator divergence when violated. Because these errors are difficult to model analytically, rigorous testing with real or realistically rendered imagery is essential prior to deployment.

---

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/8.jpg" title="Visual navigation and data association concept" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/7.jpg" title="Feature detection and labeling example" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  Conceptual overview of visual navigation, feature detection, and data association using rendered imagery.
</div>

---

## MATLAB–Python–Blender Pipeline Architecture

When real imagery is unavailable, the pipeline uses **Blender** to render images of the expected environment. Blender was chosen due to its open-source nature, ability to run without high-end GPUs, and its built-in **Python API**, which allows full programmatic control of rendering.

The three-program architecture was selected for the strengths of each tool:
- **MATLAB**: navigation algorithms, estimation, and experiment orchestration  
- **Blender**: image rendering from specified camera poses  
- **Python**: feature detection and data association using modern computer vision libraries  

Communication between programs is handled using **socket servers**, enabling two-way messaging and allowing the pipeline to scale across multiple machines if needed.

The automated process proceeds as follows:
1. MATLAB sends a pose vector to Blender via Python  
2. Blender sets the camera pose and renders an image  
3. Python detects and associates features in the rendered image  
4. Labeled feature pixel coordinates are returned to MATLAB  

This closed-loop design enables large-scale, repeatable testing of navigation algorithms under controlled conditions.

---

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/9.jpg" title="MATLAB–Python–Blender pipeline diagram" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  High-level architecture of the automated MATLAB–Python–Blender visual navigation testing pipeline.
</div>

---

## Pipeline Implementation and Sample Run

The pipeline is distributed as a repository containing:
- A MATLAB script for pose input and navigation processing  
- A Blender `.blend` file containing the environment model and embedded Python API script  
- Python-based feature detection and data association routines  

During execution, Blender runs continuously in a listening state while MATLAB sends pose vectors for rendering. Rendered images are saved automatically and passed to Python for processing. Status updates and file paths are communicated back to MATLAB, allowing seamless integration into existing workflows.

A typical sample run demonstrates:
- MATLAB-defined pose input  
- Blender-rendered imagery of the environment  
- Feature detection and labeling overlaid on the rendered image  

This workflow enables systematic testing across large pose sets without manual intervention.
---

## Applications and Impact

Although initially developed for aerospace navigation and extraterrestrial terrain analysis, this pipeline has broad applicability across:
- Robotics and autonomous vehicles  
- Visual SLAM and vSLAM research  
- Simulation-based algorithm validation  
- Perception system stress testing  

By automating image generation and data association, the pipeline enables deeper insight into estimator performance and failure modes, supporting more robust autonomy system development.

---

## Outcome

This project delivered a **fully automated, extendable testing pipeline** for visual navigation algorithms, bridging MATLAB-based estimation frameworks with modern rendering and computer vision tools. The system significantly reduces the barrier to large-scale testing and provides a flexible foundation for future research in autonomy, robotics, and aerospace navigation.
