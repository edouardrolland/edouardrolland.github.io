---
title: MSc Thesis - Presentation
date: 2023-06-06
categories: [MSc Thesis]
tags: [Academic, Studies, Bristol, Machine Vision, Robotics, Drone, Volcanoes, Plume, trajectory planning, Visual Servoing]     # TAG names should always be lowercase
comments: true
---

<style>
  p {
    text-align: justify;
  }
</style>

This article details the presentation and preliminary studies leading up to the completion of my Master's thesis conducted at the University of Bristol.
The University of Bristol has been involved in past campaigns collecting volcanic ashes using drones, as showcased in the following video.

<div style="display: flex; justify-content: center; align-items: center;">
  <iframe width="560" height="315" src="https://www.youtube.com/embed/9kC0jaVCuUE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>
<center>
Volcanic ash collection thanks to a fixed wing drone
</center>

All the different campaigns were conducted at the Fuego Volcano located in Guatemala.

# Aims and Objectives of this MSc Thesis

This project aims to understand how to collect ashes at a single point
in the smoke plume’s space using machine vision and more particularly
visual servoing.

## Core Objectives

-   Create and label a database of volcano plume images from existing
    video of Fuego volcano in Guatemala.

-   Train an agent on the database and test on existing plume video.
    This could be on stills or video.

-   Create a predictor for the location of the plume taking into account
    the wind direction.

-   Create and simulate a visual servoing method to bring the aircraft
    to an appropriate point in the plume.

## Stretch Objectives

- To design a forebody for BUDDI of less than 800g (Bristol University
    Drone Design Initiative) to house the camera, a computing bay and a
    sample collector.

- To develop code which automatically records the location of the
    samples that are taken based on the machine vision and recorded
    aircraft tracks/location.

The stretch objectives are designed to allow me to add a hardware dimension to this project. The main objectives only involve software development. 
With a strong interest in combining hardware and software creation, the CAD (Computer-Aided Design) part 
will enable me to showcase the skills I have developed in the past.

# Motivation

## Why study volcanic ash plumes ? 

Volcanic eruptions can release ash, water vapour, and gas into the
atmosphere, impacting local populations and air traffic. For instance,
the eruption of Eyjafjallajökull in 2010 led to the largest air traffic
disruption in the past decade, with 48% of European air traffic
suspended {% cite Volcano_Island bolic2011eruption %}. Studying the chemical
composition and atmospheric dispersion of volcanic ash allows us to
monitor the evolution of eruptions and evaluate potential impacts on air
traffic and the environment {% cite gouhier_2019%}.

<div style="text-align: center;">
    <a id="dispersion_model"></a>
    <img src="https://www.tripsavvy.com/thmb/elNc6VQdMNmUS9yay30yAddk3_k=/1500x0/filters:no_upscale():max_bytes(150000):strip_icc()/GettyImages-115183082-59de6ff0af5d3a0010396501.jpg" style="width: 50%; display: block; margin: 0 auto;" alt="dispersion_model">
</div>

<div style="text-align: center;">
Fig.1 Eyjafjallajökull eruption, from https://www.tripsavvy.com/
</div>

The impact of volcanic eruptions on air traffic is assessed using two
main tools: satellite remote sensing and advection-diffusion dispersion
models {% cite acp-11-4333-2011 %}. However, to generate reliable forecasts
using these predictive models, measuring the particle size distribution
(PSD) of the ash present in the plume is crucial. Although this
parameter can be determined through satellite measurements {% cite article_ash_model %}, acquiring data through optical remote sensing can
be challenging under certain weather conditions and introduce latency {% cite PRUDENTE2020100414 %}. In-situ sampling within the plume provides a
method for greater operational flexibility, allowing for better
anticipation of the impact of an eruption.

## Why take ash plume samples with a drone ?

As sampling must be done directly inside the smoke plume, it appears
dangerous to use a human-crewed aircraft. Ashes can have catastrophic
consequences on the engines, and ballistic shots near the crater can
damage the airframe {% cite article_russe %}. Collecting smoke plume samples by
drone appears to be the preferred solution. The endurance and range of a
fixed-wing drone allow these models to perform operations over long
distances. Thus, the team of scientists in charge of the expedition can
be located several kilometres away from the site of the eruption.

## Bristol University Drone Design Initiative (BUDDI) 

The Flight Lab at the University of Bristol is actively involved in
research on using drones in volcanology {% cite watson2017spying %}. From 2017
to 2019, several expeditions were organized to the Fuego volcano in
Guatemala to test various methods of sampling plume ash. All of these
experiments were carried out using commercial fixed-wing drone platforms {% cite schellenberg2020long %}. In 2018, under the impetus of the CASCADE
program (Configuration, Analysis, and Design Exploratory), the
University of Bristol developed an open-source vertical take-off
aircraft design sized to perform volcanic surveillance missions using
the knowledge gained from experiments around the Fuego volcano {% cite david2021cascade%}. The \"Bristol University Drone Design Initiative\"
(BUDDI) model is now to be equipped with a payload that will enable it
to carry out volcanic surveillance. The latter must enable the drone to
perform sample collection in a manner analogous to the previous drones
introduced in {% cite schellenberg2020long %}, but also integrate the hardware
and software elements necessary to carry out autonomous sample
collection.

<div style="text-align: center;">
    <a id="buddi"></a>
    <img src="{{site.baseurl}}/assets/img/MSc Thesis - Presentation/Buddi.png" style="width: 100%; display: block; margin: 0 auto;" alt="Buddi drone">
</div>

<div style="text-align: center;">
Fig.2 Bristol University Drone Design Initiative, illustration from {% cite david2021cascade%}
</div>

## Autonomous coordinated plume interception {#section_1}

During the previous trips to the Fuego, the various drones used were
equipped with an onboard trajectory planning system to optimize flight
autonomy up to the summit of the volcano. The collection process was not
entirely automated, as the drone's movement through the smoke plume was
controlled manually by an operator on the ground
{% cite schellenberg2020long %}. Thus, an improvement of the systems developed
by the Flight Lab teams would be to automate the control of the drone
during the collection phases. It would reduce pilot workload and
optimize drone trajectory/autonomy in real-time, as human piloting
introduces inaccuracies and errors. Full automation of the sampling
process would increase efficiency and repeatability.

<div style="text-align: center;">
    <a id="buddi"></a>
    <img src="{{site.baseurl}}/assets/img/MSc Thesis - Presentation/plume_interception.png" style="width: 80%; display: block; margin: 0 auto;" alt="Buddi drone">
</div>

<div style="text-align: center;">
Fig.2 Plume interception conducted by the University of Bristol in Guatemala {% cite schellenberg2020long %}
</div>



The first step is to develop a robust method to allow the drone to
detect the appearance of an ash plume in the atmosphere. In previous
Fuego excursions, the drones were equipped with high-definition cameras
to record the flights. These videos provide a sufficient database to
train a machine-learning model to detect smoke plumes {% cite flightlab %}.
Nevertheless, the similarity of the clouds surrounding the volcano and
the plumes may challenge training a sufficiently accurate neural
network. However, the literature reports several similar studies:
detecting fire smoke using neural networks {% cite zhang2020dual frizzi2017detection %}. The results obtained support the
idea that this method is feasible for detecting volcanoes ash plumes. By
using a database containing both clouds and fire smoke, {% cite zhang2020dual %}
achieved a detection rate of 99.33%. Next, we will focus on implementing
the control law that allows the drone to intercept the plume by
considering its movement.

Installing a camera on the BUDDI will enable a machine-learning model to
detect plumes in flight, which can then serve as an input for the
drone's control law. However, since real testing won't be feasible
during this project, developing a numerical simulation to test the
various control algorithms envisaged becomes imperative. To numerically
simulate an interception, it will be necessary first to understand how
to model the movement of an ash plume based on physical laws. The final
part of this project will be to integrate the necessary components into
the BUDDI fuselage to implement machine vision detection, which will be
used in the next test campaigns in Guatemala in 2024.

This project is in the continuity of the Flight Lab's work, particularly
by B. Schellenberg {% cite schellenberg2020long %}. Automating drone sampling
would increase the number of samples taken during a sampling campaign.
Still, it would also make it possible to obtain an accurate estimate of
the sampling area by comparing the data acquired by the sensors. A
precise knowledge of the sampling area is important, as its distance
from the crater is a necessary parameter for using ash dispersion models {% cite acp-11-4333-2011 %}.

# Literature Review

## Use of UAVs for autonomous ash plume sampling

The potential of drones to carry out scientific missions has been known
since the emergence of this technology. Multi-rotors and fixed-wing
models have been used since the 2000s to perform Earth science missions {% cite 10.2112/JCOASTRES-D-15-00005.1 article_intro %}. The literature
reports on the first use of a drone for volcanic monitoring in 2007 {% cite mcgonigle2008unmanned %}. Since then, multirotors or fixed-wing drones
have been used in numerous volcanic surveillance missions. In 2017,
Stefano et al. used a multirotor to take ash samples during an eruption
in Indonesia. The University of Bristol Flight Lab used fixed-wing
aircraft to collect ash plume samples from 2017 to 2019 {% cite DISTEFANO201826 schellenberg2020long %}.

Several approaches have been used to collect samples directly from the
plume of smoke. The first involves manually piloting the drone to the
sampling point using line of sight or a First Person View (FPV) system {%cite mcgonigle2008unmanned%}. The second approach involves using an
autopilot to follow a pre-defined flight plan and fly over the sampling
area. This method was used to collect ash samples from the plume in 2014
at Mount Ontake {%cite mori2016volcanic %}. The Flight Lab at the University of
Bristol used a hybrid method where only the ascent to the top of the
volcano was autonomous using a real-time trajectory planner. The
sampling was carried out using FPV piloting {%cite schellenberg2020long%}.

There is no mention in the literature of autonomous plume interception.
However, similar applications to forest fires can be found: Montes et
al. present a biomimetic algorithm based on the behaviour of moths to
track smoke plumes and trace them back to the source of the fire. This
concept does not apply to our study because the algorithm is based on a
multi- copter's flying behaviour and uses a carbon dioxide sensor {% cite montes2014bio%}.

## Modelling the movement of an ash plume

In light of the elements mentioned in the core objectives, it is necessary to investigate how to
model the movement of an ash plume to achieve the most realistic
simulation possible. The ash emissions from Fuego are discontinuous. In
the work previously carried out by the Flight Lab, B. Schellenberg
modelled the movement of volcanic ash plume to optimize the trajectory
between two collection points. The movement was modelled by considering
the ash plume as a homogeneous mass of constant volume moving in the
direction and at the speed of the wind. No other physical phenomena were
taken into account {%cite schellenberg2020long%}.

The literature mentions more numerical complex models for modelling
volcanic plumes emanating from the crater. Two-dimensional integral
models are computationally inexpensive and based on the assumption that
gases and emitted particles are in thermal equilibrium with the
atmosphere. By establishing mechanical considerations, it is then
possible to model the system in the form of differential equations {%cite volcano_2 %}. Woodhouse et al. were able to model the effects of wind on
a volcanic ash plume based on the observation made during the eruption
of Eyjafjallajökull {% cite volcano_1 %}. The evolution of computing power over
the past decades has made it possible to make three-dimensional models
more complex and refined {% cite volcano_4%}. Using the 3-dimensional Euler
transport equations, Cerminara et al. were able to model the evolution
of a volcanic plume considered as a mixture of gases and dispersed
solids {%cite volcano_3 %}.

## Machine Vision for detecting plumes

To use visual detection by a camera of the plume as input for a control
law to steer the drone, it is necessary to conduct a state-of-the-art
review of associated machine vision methods. The literature highlights
the use of 2 different types of methods for detecting the presence of
smoke in an image.

### Methods based on image analysis

Several image analysis-based approaches have been proposed for detecting
the presence of smoke in images. The first approach uses colour and
statistical methods for detection {%cite MV_Color_1 %}. Ebert et al.
successfully detected smoke by analyzing temporal variations in colour
intensity {%cite MV_Color_2 %}. A second approach is based on analyzing motion
in images. Ho et al. use a motion history detection algorithm coupled
with a fuzzy reasoning system {%cite MV_Movement_1 %}. Finally, a third
approach involves analyzing textures in the image using matrix analysis
methods such as Singular Value Decomposition (SVD) or the Local Binary
Pattern method {%cite MV_Texture_1 MV_Texture_2 %}.

In the context of our application, the first two methods have
limitations. The characterization of smoke using its colour is not a
sufficiently robust parameter, as Celik et al. indicated: the smoke
colour depends on many parameters {%cite MV_Color_1 %}. Characterization based
on movement requires a fixed camera viewpoint, which will not be present
during a drone flight. Nevertheless, the method developed by
{%cite MV_Texture_1%} is claimed to be robust and insensitive to camera
motion.

### Methods based on machine learning

The literature of the last 10 years also reports deep learning methods
to detect fires more especially smoke. The most commonly represented
approach in the literature is Convolutional Neural Networks (CNNs). This
type of network is composed of several convolution layers that filter
the input data to extract important features from the image {%cite CNN_1 %}.
This type of neural network has demonstrated great performance in object
classification. As mentioned in the motivation section, they can achieve classification rates of over
98% for smoke detection problems.

Regarding the different existing architectures, Pundir et al. and Zhang
used a dual deep-learning network {%cite CNN_2 CNN_3 %}. Pundir's neural
network consists of two parts: one to extract data based on smoke
behaviour (colour, texture) and another to extract features related to
smoke movement. The features from both parts are combined to achieve
classification. This model trained with 14,000 images, achieves an
accuracy of 98.3% for close-range smoke and 91.96% for distant smoke
{%cite CNN_2%}. Han et al. used an improved LeNet-5 network model and achieved
an accuracy of 94.24% by training their model using a database of 3400
images {%cite CNN_4 %}. Zheng et al. evaluate the performance of different
architectures in the case of detecting smoke from forest fires
(EfficientDet, Faster R-CNN, YOLOV3, and SSD). It turns out that YOLO V3
enables the fastest detection (27 frame par seconds), while EfficientDet
achieves the highest accuracy (95.7%) {%cite CNN_5 %}. To reduce the training
time, it should be noted that all models used the transfer learning
method {%cite CNN_2 CNN_3 CNN_4 CNN_5 %} based on pre-trained models.

It appears that a machine vision model based on a Deep Learning model
would be a reliable way to detect smoke plumes. Using the videos
collected in Guatemala {%cite flightlab%}, it will be possible to create a
customized database to train the detection model for the specific
detection of volcano plumes in the same way as the database created by
Han to detect ship emissions {%cite CNN_4 %}.

## Machine Vision for trajectory guidance

The literature highlights the potential use of machine vision techniques
in drone applications, including autonomous surveillance, search and
rescue mapping, aerial refuelling, and industrial facility inspection
{%cite visual_1%}. Within the context of UAVs, machine vision algorithms can
be categorized into three main categories: visual localization and
mapping, obstacle avoidance, and visual servoing {%cite visual_1 visual_2 %}.
This dissertation topic focuses specifically on state-of-the-art visual
servoing techniques. Visual servoing enables the utilization of visual
data acquired by an onboard camera to provide feedback to a control loop
{%cite visual_2 visual_3 %}. Therefore, with the aid of this technique, the
detection of smoke plumes can be utilized as an input parameter to a
control law that guides the BUDDI into the plume.

Similar applications can be found in the literature. Singh et al. used
feature detection in an image to perform object tracking based on a
Viola-Jones algorithm and blob analysis {%cite visual_4 %}. Prabowo et al.
devised a visual servoing system, which empowers a fixed-wing drone to
track a target by utilizing the position of a feature in an image as an
input of the control loop. The latter makes it possible to influence the
various control surfaces of the fixed-wing drone (ailerons, elevator and
drift). The efficiency of the developed algorithms was verified through
the application of the hardware in the loop simulation (HITS) technique
{%cite visual_5%}. A purely simulation-based method was used by Aygun et al.
to test a nonlinear vision-based missile guidance law. The latter
consists of a visual servoing method used in conjunction with a
sliding-mode control strategy. The simulation conducted on MATLAB
demonstrates that the approach used allows the missile to determine a
trajectory enabling it to intercept both stationary and moving targets
{%cite visual_6%}. In the same way, a simulated nonlinear-model predictive
controller is developed by Cheng et al. to track a moving feature thanks
to a multi-copter {%cite visual_7%}. Using computer simulations and
experimental tests on a multirotor, Liang et al. were able to develop an
image-based servoing controller based on a perspective projection model
and the implementation of a velocity observer in translation by
observing features presented in the image. The quadcopter and visual
information dynamics are combined within a nonlinear controller based on
the backstepping technique {%cite visual_8%}. The literature alludes to
analogous studies where a drone can trace a path by leveraging visual
data, and nonlinear controllers seem to be the more favorable option.
The same approach can potentially be employed to design a plume
interception simulator for BUDDI by adopting a numerical method akin to
that of {%cite visual_6 %}.

# Impact Assessment

## A new tool for monitoring volcanic eruptions

In the event of the democratization of drone usage in volcanology,
scientists could access a multitude of new data, allowing them to study
previously inaccessible volcanoes to ground-based scientific teams. For
instance, the summit of Fuego in Guatemala cannot be approached within 1
km {%cite watson2017spying %}. More systematic data collection through drones
could significantly improve the accuracy of predicting future eruptions,
enabling decision-makers to implement adequate protective measures to
preserve local populations from the effects of volcanoes. Predicting
lava flows or pyroclastic surges would be particularly essential for
this purpose. Given that 1/10th of the world's population lives in an
area where volcanism can have a negative impact, improved sampling
methods around volcanoes can have a significant societal impact
{%cite brown2017volcanic%}.

If the sampling of ash by drones becomes widespread, scientists can to
perform numerous successive samplings during an eruption. These will
enable estimating the particle size distribution (PSD) much more
frequently than with satellites. As a result, dispersion models will be
updated much more quickly than with satellites and will become more
reliable. The improvement in predictions will allow better management of
the impact of volcanic ash. With better anticipation, it will be
possible to reduce disruptions to economic activities such as
agriculture, tourism, and air traffic. Local authorities and airline
companies can take prevention and preparation measures to minimize the
economic costs associated with ash emissions.

However, ethically, authorities and scientists must transparently use
drones regarding the nature of the data collected and their use.
Organizations must demonstrate responsibility in using prediction models
and be aware of the risks if the forecasts prove to be incorrect: an
underestimation of risks could make them responsible for human losses,
while overly alarming forecasts could lead to premature evacuations,
economic losses, and unnecessary trauma for populations. Therefore,
volcanology organizations and decision-makers need to address issues
related to volcanological data and the limitations of prediction models.
Under these conditions, drones will be used ethically and responsibly to
serve and protect communities.

## Long-term impact of using drones for volcanic monitoring

Volcanic eruptions are natural events that can take place over an
extended period. The University of Paris I reports that the median
duration of an eruption is 7 weeks {%cite paris %}. If multiple drones are
utilized to gather data on the eruption during this period, it may lead
to environmental issues arising from their impact. Drones used in
volcanic monitoring must cover extensive distances to reach the
volcano's summit, which can cause excessive noise pollution, potentially
disturbing animal species living in the vicinity of the volcanic area.
As a result, it is crucial to consider the impact on surrounding animal
species before initiating a prolonged monitoring campaign.

If drone-based volcanic surveillance technology continues to evolve, it
will no longer be exclusively reserved for scientists to conduct
surveys. It could also be utilized by companies offering their aerial
services and provide data to government entities for assessing the risks
of a volcanic eruption. However, this category of application remains
very specific since there are only about fifty volcanic eruptions per
year {%cite gvnt%}, and these companies will only develop in regions with
volcanic activity.

From a legal standpoint, the use of these drones for volcanic
surveillance will mainly be in Beyond Visual Line of Sight (BVLOS) mode,
which requires a declaration of operations in most countries to fly a
drone in regulated airspace. For instance, in Europe, the European Union
Aviation Safety Agency (EASA) regulates BVLOS missions using the SORA
method, which allows for the declaration of the flight zone to the
authorities and risk assessment {%cite SORA%}. This type of procedure is quite
complex to implement and time-consuming. If the feasibility of using
drones in emergencies is proven, governments will be encouraged to
establish infrastructures to simplify using of drones in BVLOS. For
example, governments could develop an Unmanned Traffic Management (UTM)
system to regulate drone flights in their territories in a manner
similar like already exists for human-crewed aircraft.

# References

{% bibliography --cited %}

