---
title: Study of the curvature of a fluidic elastomer gripper
date: 2023-06-05
categories: [Academic Projects, Bristol]
tags: [Academic, Studies, Bristol, Soft Robotics, Robotics]     # TAG names should always be lowercase
comments: true
---

<style>
  p {
    text-align: justify;
  }
</style>


This article originates from a coursework conducted at the University of Bristol, focusing on the fabrication and investigation of a Pneu-Net soft gripper architecture. 
The following video provides an overview of the operational principles of this type of gripper.

<div style="display: flex; justify-content: center; align-items: center;">
  <iframe width="300em" height="600em" src="https://www.youtube.com/embed/Lk2cIwTRDkE" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
</div>
<center>
The soft gripper in action
</center>


# Introduction : a quick literature review on fluidic elastomer grippers
<p>
Grippers are essential for robots to interact with and manipulate
objects in their environment. In industrial applications, traditional
grippers consist of rigid links and joints that deform to grip an
object. However, their structural and kinematic complexity can make
control challenging. This report focuses on a less complex alternative:
fluidic elastomer grippers. </p>

The latter are composed of an elastomer structure with an internal
network of fluidic channels. The injection of pressurised fluid inside
these channels can deform the gripper's structure, and manage its
opening and closing. The soft nature of the gripper allows it to grasp
fragile objects delicately. This characteristic has been tested in
applications such as coral sampling in the deep sea  {% cite coraux %}. Actuators
of this type can be controlled using various fluids, but the air is
preferred due to its low viscosity. This characteristic allows lower
pressure forces to be exerted within the gripper {% cite marchese2015recipe %}.

The most commonly used manufacturing method for fluidic elastomer
grippers is castable silicone moulded into 3D printed parts. The mould
allows the generation of silicon sections of different stiffnesses
allowing the deformation of the gripper when it is being pressurised. 3D
printing to produce these moulds offers numerous advantages, such as
reduced manufacturing costs, rapid prototyping, and repeatability
{% cite marchese2015recipe mosadegh2014pneumatic  %}. The scaffold-removal
method, in which internal structures are added to the elastomer and
later dissolved, can create complex shapes that cannot be achieved with
the previously mentioned technique {% cite saggiomo2015simple %}.

The most commonly used channel architecture in soft robotics is the
Pneu-Net architecture, which consists of two parts, as shown in Fig.
[1](#Pneu-Net). The first
part is designed to be expandable and contains the desired channel
structure and expansion chambers. The second part is reinforced with a
non-expandable material, such as fabric or fibres. 

<a id="Pneu-Net"></a>
![Pneu-Net Architecture]({{site.baseurl}}/assets/img/soft_robot/pneunet.jpg){#Pneu-Net}
_Fig. 1 Pneu-Net Architecture - Illustation from {% cite mosadegh2014pneumatic %}_



When pressurised, the first part expands, stretching the walls of the
chambers in the expandable section. This deformation causes the entire
actuator to flex {%cite marchese2015recipe ilievski2011soft %}.

Different manufacturing methods and architectures were also explored.
Wang et al. were able to develop a 3-fingered gripper composed entirely
of 3D-printed parts {%cite 3-doigts %}. Yang et al. contributed by using the
contraction principle to operate a gripper's opening and closing. Their
method is to apply negative pressure in a solid molded with silicone
that contains cavities. Under the pressure, the cavities retract and
deform the material. The solid is then equipped with extensions that act
as fingers. The contraction and relaxation of the material allows the
modification of the space between the extensions, thus allowing the
opening and closing of the gripper {% cite contraction %}. The article {% cite composite %} presents a gripper composed of several prestrained fluid composite actuators. Each actuator uses a restraining layer made of composite to obtain a pre-curved equilibrium shape. The other layers made of elastomers flatten the composite part when pressure is introduced into the actuator. Unlike previously presented technologies, this method has the advantage that the system's equilibrium position corresponds to the closed gripper position.

The literature includes several studies proposing various methods to improve the efficiency and intelligence of fluidic elastomer grippers. For instance, Glick et al. used biomimicry to enhance gripping performance by creating a gripper consisting of two Pneu-Net actuators coated with a gecko-inspired adhesive. This approach enabled the gripper to improve its grasping abilities {% cite geckos %}. The manufacturing process of grippers also allows for the direct integration of sensors into the gripper structure to make them intelligent. For instance, in {% cite curvature %}, curvature sensors were integrated into each finger of a gripper to evaluate their curvature during object grasping. Similarly, {% cite resistif %} integrated resistive deformation sensors and capacitive proximity sensors into a Pneu-Net gripper to enable it to detect the size of the grasped objects. Yang et al. have successfully developed a 3D printed pneumatic actuator inspired by the kinematics of the human finger. The actuator can be printed in one piece and contains pressure and position sensors integrated at each joint. This innovation opens up possibilities for applications requiring closed-loop control {% cite last %}.


# Gripper Fabrication

The gripper design, provided by the University of Bristol, features the
Pneu-Net architecture, which consists of 8 chambers located on either
side of the air supply. The gripper's inextensible layer is mainly made
of J-cloth fabric, while its extensible layer is made of Eco Flex00-30
silicone material {% cite EcoFlex %}. It should be noted that the mechanical
properties of J-Cloth are anisotropic : it can stretch more easily in
one direction than another.

## Materials provided

To fabricate the gripper, the University of Bristol provides a kit that
contains the following elements:

-   Ecoflex 00-30 (Composed of two liquids (A and B) to be mixed
    together to obtain silicone.)

-   Nitrile rubber gloves, Blue paper (for cleaning)

-   Mixing sticks and a Mixing pot

-   A 3D printed mould (Shown in Fig.
    [2](#3D - mould))

-   Syringe, a connector and tubing

-   J-cloth (A type of absorbent fabric whose initial application is
    found in the household domain)



<div style="text-align: center;">
    <a id="3D - mould"></a>
    <img src="{{site.baseurl}}/assets/img/soft_robot/Vue_3D.png" style="width: 50%; display: block; margin: 0 auto;" alt="3D View of the mould">
    Fig. 2 CAD model of the 3D printed mould
</div>

## Safety conditions

Even though both components used in the silicone fabrication process are
not skin irritants, as a preventive measure, all handling involving
liquid Ecoflex will be carried out with nitrile gloves.

## Fabrication process

All the instructions for making the gripper are provided in a video made
by Dr. Alix Partridge. The instructions can be summarized in the
following three steps:

-   *Silicone Fabrication Process :* To make silicone, the same process
    will always be used: mix each EcoFlex component in equal proportions
    in a mixing pot, then pour the resulting mixture into a syringe. By
    plugging the end of the syringe, and pulling the plunger, it is
    possible to create vacuum. This will eliminate air bubbles in the
    liquid. This process should be repeated at least 10 times.

-   *First step :* To start, cut a piece of J-cloth slightly larger than
    the mould surface and place it on a smooth surface, like laminated
    cardboard. Ensure that the direction in which the J-tissue can
    stretch is aligned with the longitudinal axis of the mould. Also be
    sure to position a piece of tube at the designated location in the
    centre of the mould. Then make silicone using the method described
    above. Pour the silicone into the mould being careful not to
    introduce air bubbles. The remaining silicone can be applied to the
    J-Cloth using the supplied mixing sticks. Let the silicone dry for a
    minimum of 4 hours.

-   *Second step :* To start, demold the silicone and peel off the
    J-Cloth from the smooth surface. Then, cover the base of the molded
    part with a thin layer of liquid silicone using your finger. Coat
    the surface of the J-Cloth that was in contact with the
    plastic-coated cardboard with silicone as well. Next, place the two
    coated layers in contact, taking care to avoid the formation of air
    bubbles at the joint. After completing this step, it is important to
    allow the silicone to dry for 4 hours.

-   *Third step :* Connect the gripper tube to the syringe using the
    adapter, pressurize it and check for proper functioning

# Experimental design

In the framework of this project, two main experiments are envisioned:
the first one focuses on studying the curvature of the gripper as a
function of the injected air volume, and the second one aims to
determine the gripper's performance in grasping multiple types of
objects.

## Curvature Study

### Hypothesis

By compressing the gripper with different volumes, it is observed that
the curvature of the gripper appears to approach that of a circular arc.
To experimentally test this hypothesis, a measurement method is
established to record the gripper's curvature using a camera. A circular
fitting method will be used to verify if the curvature of the gripper
can be inscribed in a circle. If this hypothesis is validated through
the experiment, it will also be possible to plot the gripper clamping
radius evolution law as a function of the injected air volume.
[]{#part:hypothese label="part:hypothese"}

### Setting up the test bench

For precise measurements, a test bench is utilized to hold the gripper
fixed during compression. This setup ensures a constant fixed position
of the camera and gripper for all tested air volumes. The test bench, as
shown in Fig. [3](#test_bench), also includes a graduated ruler that serves as
a scale during machine vision analysis. A black background is placed to
aid the machine vision procedure, and red pinheads are evenly
distributed along the gripper for subsequent identification of its
curvature (Fig. [3](#test_bench)). The machine vision technique employed is
elaborated in a following section

### Proposed experimental protocol

The following method is used for each volume from 0 to 60 ml with a step
of 5 ml:

-   The considered volume is injected into the gripper and a paper clip
    is used to clamp the tube and keep the gripper in a fixed position.

-   A scene acquisition is performed using a camera, which is a
    smartphone held on a tripod.

-   The coordinates of the gripper pinheads are extracted using a
    machine vision algorithm, which provides pixel coordinates in the
    image reference frame.

-   The circle-fit library {%cite pypi %} is used to determine the parameters
    of the circle (center coordinates and radius) that best fits all the
    gripper points. The accuracy and precision of the model are
    evaluated using the value of the residual error provided by the
    library. The results obtained are returned in pixels, the scale
    present on the photo allows to convert the found values into
    centimeters.

-   The gripper markers and the fitting circle are displayed on the same
    graph.

First, these data will allow us to study the evolution of the residual
error according to the injected air volume, in order to check if the
gripper curvature can be approximated by a circle.

### Description of the machine vision method used

The method used is based on the elements provided in the document
{% cite QiConn-2023 %}. For each image to be processed, the same method is
applied. The different functions used come from the Python module OpenCV
which allows image processing {%cite opencv_library %}. The coordinates of the
gripper points are stored in a list and are subsequently used for
interpretations. The steps of the machine vision algorithm are described
in Fig. [3](#test_bench).



<div style="text-align: center;">
    <a id="test_bench"></a>
    <img src="{{site.baseurl}}/assets/img/soft_robot/Machine_Vision.png" style="width: 75%; display: block; margin: 0 auto;" alt="test bench">
    Fig. 3 Test Bench made of Legos
</div>

The entire code used in this project is available in the dedicated
Github repository which can be found
[here](https://github.com/EdRlld/Soft_Robotics_Machine_Vision).

## Study of the grasping capability of the soft gripper

### Hypothesis

An assumption is made that the gripper is capable of lifting a wide
range of differently shaped objects. The following experiment aims to
test the gripper's ability to lift various types of objects.

### Proposed experimental protocol {#part:exp2}

The objective of this experiment is to study the configuration and
grasping capability of the gripper on various everyday objects. The
experimental protocol involves the following steps:

-   Select an object and measure its mass.

-   Place the object on a flat surface.

-   Position the gripper on the object and compress the syringe.

-   Attempt to lift the object while taking a photograph of the
    configuration.

# Results and Analysis

## Curvature Study

### Machine Vision Results

The machine vision method is applied and allows obtaining the gripper's
shape for different volumes as presented in Fig.
[4](#fig:Gripper_gaits). For display convenience, only half of
the tested volumes are shown.

<div style="text-align: center;">
    <a id="fig:Gripper_gaits"></a>
    <img src="{{site.baseurl}}/assets/img/soft_robot/Extraction_of_gripper_gaits.svg" style="width: 75%; display: block; margin: 0 auto;" alt="gripper gaits">
</div>

<div style="text-align: center;">
Fig.4 Gripper gaits
</div>

It is possible to observe that when the volume is zero (the gripper is
not compressed), it is already curved due to the effect of gravity on
the soft material.

### Circular fitting results and interpretations

Using the different coordinates of the points, a circular fitting is
performed for each volume value. Fig.
[5](#fig:Circular_fitting) shows 4 examples of circular fitting.


<div style="text-align: center;">
    <a id="#fig:Circular_fitting"></a>
    <img src="{{site.baseurl}}/assets/img/soft_robot/circular_fitting.png" style="width: 50%; display: block; margin: 0 auto;" alt="Circular Fitting">
</div>

<div style="text-align: center;">
Fig.5 Circular Fitting
</div>

As the quantity of injected air increases, fitting a circle to the
curvature of the gripper becomes more difficult. This is supported by
the residual error curve (Fig.
[6](#fig:Circular_error)), which represents the root mean square
error between data points and the circumference of the regression circle
{% cite pypi %}. The gripper's curvature can be approximated by a circular arc
from 0 to 25 ml, with a residual error below 1 mm. However, the residual
error increases beyond 30 ml, indicating that the curvature cannot be
approximated by a circular arc. Thus, presenting the clamping radius as
a function of the gripper is not relevant from 0 to 60 ml. The
hypothesis stated in section
The hypothesis part is not validated.

<div style="text-align: center;">
    <a id="#fig:Circular_error"></a>
    <img src="{{site.baseurl}}/assets/img/soft_robot/Residual_Error_display.svg" style="width: 75%; display: block; margin: 0 auto;" alt="#fig:Circular_error">
</div>

<div style="text-align: center;">
Fig.6 Residual error as a function of injected
volume
</div>

### Study of another parameter

It is not possible to accurately represent the entire curvature of the
gripper using a circular arc. However, an appropriate parameter is being
sought to quantify this curvature. Therefore, the concept of the
\"corrected clamping radius\" is introduced, which corresponds to the
radius of the circle passing through the center and the gripper ends as
shown in Fig. [7](#fig:bending_angle). This parameter indirectly quantifies the
size of objects that the gripper can grasp. Finding a model to represent
the evolution of this parameter is relevant as it could serve as a
control law in a more intricate system.

<div style="text-align: center;">
    <a id="#fig:Circular_error"></a>
    <img src="{{site.baseurl}}/assets/img/soft_robot/Bending_Angle.png" style="width: 50%; display: block; margin: 0 auto;" alt="#fig:bending_angle">
</div>

<div style="text-align: center;">
Fig.7 Definition of the Corrected clamping
radius
</div>

Thus, the circular fitting method is applied to only 3 points. Given the
number of points considered, circular fitting is perfect, and for each
volume value, the corrected clamping radius is derived. The resulting
graph is presented in Figure
[8](#fig:bending_linear).

<div style="text-align: center;">
    <a id="#fig:bending_linear"></a>
    <img src="{{site.baseurl}}/assets/img/soft_robot/Circular_Regression_with_3_points.svg" style="width: 65%; display: block; margin: 0 auto;" alt="#fig:bending_linear">
</div>

<div style="text-align: center;">
Fig.8 Evolution of corrected clamping
radius
</div>

The experimental points obtained allow a modeling of the corrected
clamping radius (CCR) as a function of the volume. A polynomial
regression is applied to the data, and it turns out that a 5th order
regression yields the best correlation coefficient without overfitting.
The derived equation is shown in
Fig.[8](#fig:bending_linear).

## Study of the grasping capability of the soft gripper

By using the experimental protocol mentioned, the
gripper lifted the different objects presented in Fig.
[9](#sousou): a cardboard box,
a 3D printed piece, a Rubik's Cube, and a meter.

The gripper was found to be able to grasp a range of objects as long as
their weight is less than 120g. Beyond this threshold, the gripper
slides and is unable to hold the object. In addition, the shape of the
gripper does not match that of the object it grabs: only the two ends
are in contact.

To improve the performance of the gripper, it could be considered to add
a rough surface like sandpaper to ensure better adhesion, similar to the
work done by {% cite geckos %}.

<div style="text-align: center;">
    <a id="#sousou"></a>
    <img src="{{site.baseurl}}/assets/img/soft_robot/objects_tests.png" style="width: 50%; display: block; margin: 0 auto;" alt="#sousou">
</div>

<div style="text-align: center;">
Fig.9 Various tested objects
radius
</div>

# Discussion

## Improvement suggestions on the fabrication method

### Tubing problem

During the manufacturing process, a difficulty arose during the
demolding stage, resulting in the tube being held in the mold and
detachment from the silicone part, as shown in Fig.
[10](#fig:probleme){reference-type="ref" reference="fig:probleme"}. I
attempted to remedy the situation by using glue to reattach the tube,
but the physical properties of the silicone hindered the adhesion of the
glue, rendering this solution ineffective.

<div style="text-align: center;">
    <a id="#fig:probleme"></a>
    <img src="{{site.baseurl}}/assets/img/soft_robot/probleme_1.jpg" style="width: 50%; display: block; margin: 0 auto;" alt="#fig:probleme">
</div>

<div style="text-align: center;">
Fig.10 Fabrication problem encountered
</div>

To address the difficulty at hand, the manufacturing process of the
molded part had to be restarted with various precautions taken. Abrasive
paper was utilized to sand the outer surface of the tube for better
silicone adhesion, and the part of the mold that held the tube was also
sanded to make detachment easier. Once the tube was properly positioned
in the mold, the tube base was degreased with 90% alcohol. With these
measures in place, the molded part of the gripper was successfully
manufactured without any detachment issues.

### Air leakage issues

During the manufacturing process, another issue was observed which
concerned air leakage during the final gripper testing. These leaks were
found at the junction between the J-Cloth and the molded part. An
additional step was added to the process to overcome this issue. At the
end of the second step of the manufacturing process, a silicone sealant is applied all around the
molded part to prevent leakage. The sealant is depicted in yellow in
Fig. [11](#fig:joint).


<div style="text-align: center;">
    <a id="#fig:probleme"></a>
    <img src="{{site.baseurl}}/assets/img/soft_robot/joint.svg" style="width: 40%; display: block; margin: 0 auto;" alt="#fig:joint">
</div>

<div style="text-align: center;">
Fig.11 Addition of a seal to ensure tightness.
</div>



## Suggestion for design improvement

The current gripper could only limit two degrees of freedom during the
grasping experiment due to its two contact points. To improve this, a
feasible solution would be to add a new part to the gripper that blocks
all three degrees of freedom, enhancing grasping quality and preventing
object movement on all axes. Increasing the contact surface between the
gripper and the object by adding a third contact point would also
improve grip. To achieve this, we modified the existing gripper's CAD
model, creating a three-fingered gripper with 120-degree spacing between
each finger. The resulting 3D model was then printed (Fig.
[12](#fig:3pince)).

<div style="text-align: center;">
    <a id="#fig:3pince"></a>
    <img src="{{site.baseurl}}/assets/img/soft_robot/3parts.jpg" style="width: 40%; display: block; margin: 0 auto;" alt="#fig:3pince">
</div>

<div style="text-align: center;">
Fig.12 Gripper design proposal
</div>


A silicone shortage prevented full fabrication of the designed gripper
for performance testing and validation of previous hypotheses. To
address this, an extension of this work could involve repeating the
grasping experiment using the new gripper design and quantifying
performance differences between the original and new designs.

# Conclusion

This project allowed for the discovery of theoretical and practical
concepts related to fluidic elastomer grippers, with a focus on the
Pneu-Net architecture. The curvature of the gripper during compression
can only be considered as an arc of a circle in the volume range of 0 to
25 milliliters. By introducing the parameter of corrected clamping
radius, it was possible to establish a polynomial relationship between
this parameter and the injected air volume. It should be noted that the
law modeled is specific to the gripper fabricated in this report.
Indeed, variations in fabrication can modify the curvature behavior of
the gripper. The gripping capacity of the gripper was also investigated,
demonstrating its ability to grasp various objects of different shapes
and masses. Finally, design and manufacturing improvements were proposed
for the gripper.

{% bibliography %}



