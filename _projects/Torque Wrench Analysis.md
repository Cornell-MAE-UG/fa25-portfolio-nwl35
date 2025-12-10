---
layout: project
title: Torque Wrench Analysis - Mechanics of Materials
description: Class project with CAD, ANSYS FEM Analysis
technologies: [Python, Autodesk Fusion, ANSYS Workbench]
image: /assets/images/Title 3270.png
---


The final project for my MAE 3270 Mechanics of Engineering Materials class was to design a 3/8" drive torque wrench rated for 50 ft-lb of torque (600 in-lb), required to attain at least 1.0mV/V strain gauge voltage near the drive, fully reversible torque for 10^6 cycles, safety factor of 4 for yield failure, safety factor of 2 for crack growth from an assumed crack depth of 0.04 in, and fatigue stress safety factor of 1.5.


## **CAD Model Dimensions**

I created an interated design based on a provided base model in Fusion. The model includes a 3/8" drive and location for a strain gauge, in addition to basic components such as the handle and a grip extension to apply the torque from.

![Torque Wrench Dimensions]({{"/assets/images/3270 CAD Dimensions.png" | relative_url}}){:style="width:500px;"}

Key dimensions:
- Overall length: 16.36 in
- Length from force application point to center of drive L: 13.5 in
- Width h: 1 in
- Height b: 0.75 in
- Length from center of drive to strain gauge c: 1 in
- Grip handle length: 2.36 in (60mm)


## **Material Selection**

I chose P4 Tool Steel for the wrench, since it was also in the Tool Steel category and compared with the M42 Tool Steel used in the base model. Also, it was cheaper per lb while still retaining similar strength and material properties to the M42 steel.

Material properties:
- Young's Modulus (E): 29.7e6 psi
- Tensile Strength: 305 ksi
- Fracture Toughness (K_IC): 16.7e3 psi*(in)^0.5
- Fracture Strength: 81.1 ksi for 10^7 cycles
- Poisson's Ratio: 0.285

For the 50ft-lb torque loading, the wrench possesses the following saftety factors:
- Yield/strength: 63.54 (minimum 4)
- Crack growth: 8.76 (minimum 2)
- Fatigue: 16.90 (minimum 1.5)


## **Loads and Boundary Conditions, FEM Analysis**

In the ANSYS software, a 0 displacement condition was applied to the outer faces of the 3/8" drive, and the force was applied at the end of the wrench before the extended grip handle. Force was calculated from the torque/moment, F=M/L.

![FEM Loads and Boundary Conditions]({{"/assets/images/3270 FEM Loading.png" | relative_url}}){:style="width:500px;"}


## **Normal Strain Contours, FEM Analysis**

Pictured are the contours from the normal strain solution.

![Normal Strain]({{"/assets/images/3270 Normal Strain ANSYS.png" | relative_url}}){:style="width:500px;"}


## **Maximum Principal Stress, FEM Analysis**

Pictured are the contours from the maximum principal stress solution.

![Max Principal Stress]({{"/assets/images/3270 Max Principal Stress ANSYS.png" | relative_url}}){:style="width:500px;"}


## **FEM Results Summary**

From the FEM Analysis:
- Maximum Normal Stress: 55.7 ksi
- Load Point Deflection: 0.03 in
- Strain at gauge location: 40 microstrain

From hand calculations:
- Maximum Normal Stress: 48 ksi
- Load Point Deflection: 0.02 in
- Strain at gauge location: 149.64 microstrain

Normal stress differs by 16%
Load point deflection differs by 33%
Strain differs by 73% (a lot!)


## **Torque Wrench Sensitivity**

From hand calculations, strain gauge output should be 157.13 mV/V.

Using the FEM strain value of 40 microstrain and the output equation output=(1000)(2.1)(strain)(0.5), where 2.1 is the strain gauge factor and 0.5 indicates the half-bridge configuration:

FEM strain output: 42 mV/V, which still exceeds minimum output of 1 mV/V.

## **Strain Gauge Selection**

Using the DwyerOmega SGD-2/350-LY43 would fit the dimensions required of this project. This gauge is a miniature linear pattern, solder pad gauge with carrier length 7.6 mm, carrier width 5.8mm, grid length 2mm, and grid width 2.5mm. Purchase link can be found at https://www.dwyeromega.com/en-us/linear-strain-gages/SGD-LINEAR1-AXIS/p/SGD-2-350-LY43.

![Strain Gauge]({{"/assets/images/3270 Strain gauge.png" | relative_url}}){:style="width:250px;"}