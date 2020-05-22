
# IcebergExplorerROV
This is a public repository for the Oregon State University ECE 44x Iceberg Explorer ROV Project. The client of this project is Dr. Jonathan Nash of Oregon State University 

# Table of Contents
- [Overview](#overview)  
- [Iceberg Attachment Overview](#attachment)
- [Block Diagram](#bd)
- [Heating/Melting System](#heating)
  - [Arms](#arms)
  - [Heating Element Simulations](#heat-sim)
- [Heating Power Supply System](#power)
  - [DC to AC Inverter](#dcac)
  - [DC to DC Converter](#dcdc)
  - [Analysis](#panalysis)
  - [Design](#p-design)
- [Wireless Control](#wireless)
  - [Computer Setup How-To](#w-computer-howto)
  - [Router Setup How-To](#w-router-howto)
- [Next Steps](#future-work)
  - [Power Supply PCB](#pwr-pcb)
  - [Melting Attachment System](#melt-attach)
  - [Software Simulation](#sw-sim)
  - [Hardware Simulation](#hw-sim)
  - [Battery Pack Design](#bp-design)
  - [BlueRov2 Motor Configuration](#motor-conf)
  - [Need for a Mechanical Engineer](#mech)
  - [Tool Arm Design](#tool-arm)
  - [Sensor Selection](#sensor)
  - [Additional Enclosure Design](#add-enclosure)
  - [Controls Design](#ctrls)
  - [Attachment Arm Design](#attch-arm)
  - [BlueROV2 Deployment System](#deploy)
- [Conclusion](#conclusion)
- [FAQ](#faq)


<a name="overview"></a>
# Overview

The goal of this project was to modify a [BlueRov2](https://bluerobotics.com/store/rov/bluerov2/) to add the capability to:
- attach to an iceberg and hold itself securely in place
- take measurements of the rate at which the iceberg was melting

The primary development that took place between the 2019-2020 school year focused on designing and prototyping of the first capability -- to attach securely to an iceberg. Additionally, our team created requirements and design concepts for the entire system that could be useful going forwards. 

<a name="attachment"></a>
# Iceberg Attachment Overview

When our ECE team was in its brainstorming phase, we decided to forgo physically drilling into the ice, an idea inspired by [ice climbing equipment](https://www.rei.com/product/860670/petzl-laser-speed-ice-screw), to a much more mechanically simple method of melting into the ice and refreezing the hole created around our attachment points. For further information, including pattents that cover similar designs used previously, consult the written report on [Iceberg Attachment](TODO). To accomplish this, the design was split into subsystems for the ECE team to work on.

<a name="bd"></a>
## Block Diagram

**INSERT FINAL PICTURE HERE**

<a name="heating"></a>
## Heating/Melting System

After experiments with a small soldering iron melting into ice and a larger, copper tube heated by an electric water heater, and calculations outlining the energy needed to melt into a unit volume of ice, we decided that the best type of heater for this would be a [cartridge heater](https://www.mcmaster.com/heaters/heaters-for-plates-molds-and-dies/insertion-heaters-for-plates-molds-and-dies-7/) -- which is the best option when considering the need for a small diameter heating element. This was due to the additional heat (power) needed to melt a unit volume as the area increased with diameter. Additionally, the length of the heater should be as short as possible to prevent heat from dissipating from the area that is not touching the ice on initial insertion. For the first prototype, a heating element was enclosed in a copper sheath and attached to one end of a 1m long carbon fiber tube (we called it an 'arm'); the other end of the carbon fiber rod was attached to the ROV. There were three of those arms that would then melt into the iceberg and hold the ROV in place. The next prototype should select heaters (doesn't necessarily need to be cartridge heaters) that minimize length and diameter.

<a name="arms"></a>
### Arms

<a name="heat-sim"></a>
### Heating Element Simulations


<a name="power"></a>
## Heating Power Supply System

After considering options for power and realistic battery storage, we have two ideas for power supply architectures:
- DC to AC inverter
- DC to DC converter

There are advantages and disadvantages to both achitectures that will be discussed in the following sections.


<a name="dcac"></a>
### DC to AC Inverter

Advantages:
- Readily available in modules
  - Adds simplicity
- Low cost

Disadvantages:
- Large size
- Modules are not customizable for individual use cases


<a name="dcdc"></a>
### DC to DC Converter

Advantages:
- Small sizes can be achieved
- Customizable for our application
  - We can add additional DC sub-supplies for additional hardware (microcontrollers)

Disadvantages:
- Higher cost
- Additional complexity (design our own)
- Modules are not as readily available

<a name="panalysis"></a>
### Analysis

There is still merit to debating which advantages take precidence over the disadvantages, but at this point in time space and ability to customize our power supply to fit our evolving designs. Due to these constraints, we have decided to create a custom DC to DC converter with help from [TI's Power Designer](https://webench.ti.com/power-designer/switching-regulator). 

<a name="p-design"></a>
### Design
**TODO: Add link to PCB design and description.**

<a name="wireless"></a>
## Wireless Control

<a name="w-computer-howto"></a>
### Computer Setup How-To

<a name="w-router-howto"></a>
### Router Setup How-To
**Update for long range WiFi system**

<a name="future-work"></a>
# Next Steps

The system in its current state is by no means feature complete. There are some key features that still need to be implemented by future teams. The goal of this section is to pave the pathway for an ECE group to work on this project in this future and bring it to completion.

<a id='pwr-pcb'></a>
### Power Supply PCB

Our team switched our power supply design to a 12V DC to 120V DC converter at the end of our project after building a prototype with a 12V DC to 120V AC inverter. The reasons for doing so are listed in [Heating Power Supply](#power). However, in switching, our team did not have enough time to:
- Lay out components on a PCB board
- Get the board fabricated and assemble the PCB
- Do preliminary testing

Our team did develop a schematic in KiCad for a potential design, but at this point there would be merit in starting from the ground up as there were additional power supply requirements (9V DC bus) that were recently added. 

#### Recomendation: 

Our teams recomendation is to research power topologies that will allow for efficient conversion from 12V DC to 120V DC that also allows for expansion to lower voltage power needs (implement a 9V DC bus or add easy access to the 12V DC bus for external conversion). Most importantly, the circuit should be simulated to verify that it can, in fact, produce the necessary power output to drive the melting attachment plus any secondary devices. This simulation would be most effective if it was implemented in tandem with the [Hardware Simulation](#hw-sim) component. 

#### Resources:

[Example 12V DC to 120V DC Circuit](http://www.circuitstoday.com/12v-to-120v-dc-dc-converter)


<a id='melt-attach'></a>
### Melting Attachment System

The Melting Attachment System might be the most complex yet important part of the system we tried to tackle. Through our prototypes, we've found a fiew rules of thum to adhere to when implementing this device. There is much more technical engineering to do for this device! We were not able to complete the melting attachment system because prototyping a mostly mechanical system was unfortunately not something our team was properly prepared to deal with. If there is someone with a good, in depth, knowledge of thermodynamics (fluid thermo), they would be great at this part!

#### Recomendation: 

There are some pattents that would be useful to view for this specific system. In its current state, I do not think it will successfully attach the ROV to the iceberg because:
- 1.) We haven't tested a heating system in a large body of water (you can think of this a big heat sink).
- 2.) While ice below zero does solidly refreeze over the attachment system, we are not exactly sure if the ice is cold enough. 

Therefore, there should be more research and experimentation to build a prototype that has `active cooling` such as a Peltier plate (uses power to cool back down the melted attachment to refreeze after melthing) or even a different heating elements. A rough surface (think lots of short little needles) could also bind to an icy surface and cool off fast enough to refreeze (I think). 

#### Resources:

[Report on Heating Attachment Design](https://github.com/MattShilling/IcebergExplorerROV/blob/master/Heated_Attachment_and_Enclosure_Research.pdf)

<a id='sw-sim'></a>
### Software Simulation

There is a great need for the ability to gain familiarity with the control system as well as practicing missions in a semi-realistic way. In the industry this is known as `Software In the Loop` simulation/testing and is a great way to avoid wasting thousands of dollars in equipment (and potentially even more in labor hours) if something goes wrong. Essentially, it is a way to catch things early (note: see [Hardware Simulation](#hw-sim)). Our team did not complete this because it was out of the scope for our original project. However, I can see some great use coming out of the development for SIL testing if this is going to be a multi-year project.

#### Recomendation:

There is many ways a future team could approach SIL testing, but the main concept is: come up with a way to either:
- 1.) Isolate the software components of the project and find a way to test that.
- 2.) Create a whole model of the ROV in software and simulate that.

Number two could be a project on its own, but the benefits would be immense. You could create a virtual 3D environment and ROV that would model after what a real mission would be like. People working on the project could then run virtual missions, gaining familiarity with the operation and characteristics of the device. A downside to option number two is that it will take a lot of time and teams would have to do some sort of system identification on the BlueROV2.

#### Resources:

[Software In the Loop Testing](https://www.add2.co.uk/applications/sil/)

<a id='hw-sim'></a>
### Hardware Simulation

Similar to the [SIL simulation](#sw-sim) mentioned, hardware simulation would also come with its own great benefits. However, our team did not complete this because it was out of the scope for our original project. 

#### Recomendation:

Research [HITL Simulation](#https://en.wikipedia.org/wiki/Hardware-in-the-loop_simulation) and decide if it is within the scope of the project to work on. You will need to balanace the cost of labor setting up the system as well as the cost of purchasing a completely identical system to do testing on. HITL simiulation provides a great way to develop systems in parallel.

#### Resources:

- _Enhancing Embedded Systems Simulation: A Chip-Hardware-in-the-Loop Framework_ by Christian Köhler
- _Hardware-in-the-loop simulation for a production system_ by Park, Sang C ; Chang, Minho

<a id='bp-design'></a>
### Battery Pack Design

In its current state, the system contains two separate batteries. One for powering the ROV and its motors, and the other for powering the Melting Attachment System. The issue with having two batteries is the space that having two separate battery enclosures takes up. However, there is some merit in keeping the systems separate, as isolating the ROV drive battery will prevent a [common mode failure](https://en.wikipedia.org/wiki/Common_cause_and_special_cause_(statistics)#Common_mode_failure_in_engineering) of the entire system. Our team did not complete this because it was out of the scope for our original project.

#### Recomendation:

Do risk analysis to see if the system can benefit from consolodating batteries (improvement on energy density). If you decide to carry forwards with making a battery pack, the [Power Supply PCB](#pwr-pcb) should be in the front of your mind when designing. Additionally, research into a [battery management system](#https://en.wikipedia.org/wiki/Battery_management_system) (BMS) will also be crucial.

<a id='motor-conf'></a>
### BlueRov2 Motor Configuration

The BlueRov2's current motor configuration is set up so it has maximum manueverability. However, there is some thought that the motor configuration should be changed to increase the thrust that the ROV can exert on the iceberg to more securely attach itself. Our team did not complete this because it was out of the scope for our original project.

#### Recomendation:

Investigate the impact that configuring the motors to provide more lateral thrust would have on the ROV's ability to attach itself to the iceberg (is there enough force to press the heating attachments into the iceberg?). Weigh this benefit against the reduction in stability that the ROV would incur.

<a id='mech'></a>
### Need for a Mechanical Engineer

This project has a great need for a mechanical engineer. There are many components (Melting Attachment System) that would greatly benefit from having someone with knowledge working on this project with the team. There are some mechanical engineers that worked in the same lab as our team, but had other projects to work on and could not, very understandibly, dedicate time to designing components alongside our team. 

#### Recomendation:

The project should include a mechanical engineering team or single member with in-depth knowledege of mechanical design and thermodynamics in the future.

<a id='tool-arm'></a>
### Tool Arm Design

In the future, the ROV will need to have an arm that is able to either manipulate a sensor or actuate it towards the iceberg's surface. This was originally in our project's scope, but had to be eliminated as it was not a main focus for the first year milestone of the project.

#### Recomendation:

There are some complicated components to moving parts deep underwater. There are linear actuators that are waterproof but would need to be vetted to see if they meet the waterproof and anti-corrosive requirements for the project's environment. The tool arm should be remotely controllable and precise with its movements as the measurements posed to be taken are on a very small scale.

#### Resources:

- [Waterproof Linear Actuator for Marine Applications](https://progressiveactuators.com/product-industry/marine/)

<a id='sensor'></a>
### Sensor Selection

There are a few options of sensor selection for this project. By sensors, we are talking about a sensor that is able to measure the melting rate of the iceberg. We can characterize the melting rate of the iceberg by the velocity of gas particles that are desolved from the iceberg as it melts. This was originally in our project's scope, but had to be eliminated as it was not a main focus for the first year milestone of the project.

#### Recomendation:

There are three sensors our group was looking at to fulfill the needs of our sensor were:
- [Ultra low-noise wide band hydrophone](https://www.kdpes.co.uk/product/h507a-hydrophone/)
- [Mid-frequency vector sensor](#https://www.kdpes.co.uk/product/vs-209/)
- [Low-frequency vector sensor](#https://www.kdpes.co.uk/product/vs-209/)

The nice features with these sensors is that they also include capability to help with the navigation in low visibility areas around the ice field near and up to icebergs. Dr. Nash also has sensors that could be implemented, but have not been investigated in detail.

<a id='add-enclosure'></a>
### Additional Enclosure Design

There are enclosures available from BlueROV that can satisfy the current enclosure needs of the project. However, as the project continues to add new hardware (tool arm, sensor, battery PCB) there will be increased need to re-evaluate if the current enclosures we have are suitable. Making additional enclosures was originally in our project's scope, but had to be eliminated as it was not a main focus for the first year milestone of the project.

#### Recomendation:

The Research and Implementation report done by a 2019-2020 group member could have some key insights in what it would entail to design and manufacture a robust, waterproof enclosure. As the next team continues working on the project, evaluate if creating a custom enclosure would be benefitial for its new implementations of hardware.

#### Resources:

[Report on Enclosure Design](https://github.com/MattShilling/IcebergExplorerROV/blob/master/Heated_Attachment_and_Enclosure_Research.pdf)

<a id='ctrls'></a>
### Controls Design

Currently, the system is controlled via an XBox controller connected to a laptop running [QGroundControl](http://qgroundcontrol.com/). In the future, there might need to be development on either:

- 1.) A more customized controler
- 2.) The ability to execute automated sequences of manuevers with the press of one button.

The customized controller is most likely a future-future goal as there is currently enough buttons on the XBox controller to support all forseable actions. The main work that needs to be done is figuring out how to initiate a custom sequence of commands via QGroundControl that the ROV can properly carry out. Our team did not complete this because it was out of the scope for our original project.

#### Recomendation:

There is another system layer connected to QGroundControl called [`ArduSub`](https://github.com/bluerobotics/ardusub-gitbook). There would be great value in looking through the source code of this system , understanding how it works, learning how additional features can be implemented to it, and how to replace the current firmware on the BlueROV with a custom version.

#### Resources:

- [QGroundControl GitHub Repository](https://github.com/mavlink/qgroundcontrol)

<a id='attach-arm'></a>
### Attachment Arm Design

The current design of the system specifies that the attachment arms be carbon fiber rods. There is some weaknesses to this design such as the ability to fracture when compressed, however, and it is brittle when machining to fit custom applications. Our team did not approach this concern because it was out of the scope for our original project.

#### Recomendation:

There are some routes to go here:
- 1.) Look into carbon fiber composites (coated in epoxy).
- 2.) Select another attachment arm material (aluminum).

The fiber composite would be a quick switch, but there is some research needed to be done on the corrosive resistivity of the composite material and its ability to be machined. Looking into another attachment arm material such as aluminum could also prove beneficial as there are armatures that would also serve as attachment points for sub-systems or additional sensors.

<a id='deploy'></a>
### BlueROV2 Deployment System

In the future, the BlueROV2 will need to be deployed from a remotely controlled boat. The deployment system will also need to be remotely controlled. By deploying, we mean placed into the water and turned on, ready to go on a mission. Working on this deployment system was in our project's scope, but had to be eliminated as it was not a main focus for the first year milestone of the project.

#### Recomendations:

A design and prototype should be created that has the ability to lift and lower the ROV into the water in a stable configuration (no dropping into the ocean). This could end up being quite similar to a crane. There is a NASA program called SUBSEA that has a picture with an _extreme_ example of a [similar design](https://www.eurekalert.org/pub_releases/2019-05/uori-oas052919.php) (it's lifting something much heavier). The only design difference is that it would have to be remotely operated.

<a name="conclusion"></a>
# Conclusion

<a name="faq"></a>
# FAQ


