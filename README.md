
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

### Power Supply PCB

Our team switched our power supply design to a 12V DC to 120V DC converter at the end of our project after building a prototype with a 12V DC to 120V AC inverter. The reasons for doing so are listed in [Heating Power Supply](#power). However, in switching, our team did not have enough time to:
- Lay out components on a PCB board
- Get the board fabricated and assemble the PCB
- Do preliminary testing

Our team did develop a schematic in KiCad for a potential design, but at this point there would be merit in starting from the ground up as there were additional power supply requirements (9V DC bus) that were recently added. 

#### Recomendation: 


### Melting Attachment System

### Software Simulation

### Hardware Simulation

### Battery Pack Design

### BlueRov2 Motor Configuration

### Need for a Mechanical Engineer

### Tool Arm Design

### Sensor Selection

### Additional Enclosure Design

### Controls Design

### Attachment Arm Design

### BlueROV2 Deployment System


<a name="conclusion"></a>
# Conclusion

<a name="faq"></a>
# FAQ


