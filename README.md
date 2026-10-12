# Starbie

Starbie is a personalized Starboy-themed PCB built from scratch for the Hack Club Halflife Week 1 PCB Build challenge.

This project is my first time designing a pcb taking a circuit from a schematic in KiCad to a physical Board and 
working on the code needed to bring to bring this project to life. The goal for me was to create a functional PCB 
while still adding enough unique touches to make its design unique to me.

## Project Overview
Building Starbie meant designing the circuit, laying out and routing a PCB and finally editing the software to control
the hardware. 

I split the project into three main parts:
- Schematic design: Where I took all the components and connected them to each other using Kicad
- PCB Design: Where I turned the schematic into a physical board layout, routed traces and prepared the design
  for manufacturing using KiCad
- Code: Where I edited the program on Arduino and added personal touches to the base program.

## Schematic Design
The first stage of the project was creating the circuit schematic in KiCad.

I started by installing KiCad and then setting up the required footprint and symbol libraries. Then I placed
the components into the schematic and connected them according to the circuit design. 

One of the first challenges was learning how KiCad handles component values and footprints. I also 
encountered a footprint mismatch error when a schematic symbol had more pins that its assigned physical 
footprint. After researching KiCad forums and tutorials, I worked through the component assignemnts and completed 
the initial schematic.

<img width="338" height="187" alt="image" src="https://github.com/user-attachments/assets/8b46631c-d966-47de-a254-decbc8f90cf0" />


## PCB Layout and Design
Once the schematic was finalized, the next step was to convert it into a physical PCB layout. I imported
all the components into KiCad's PCB Editor and started arranging them on a custom, star shaped board I made
on the edge cuts layer. I had to carefully plan how to fit all my components onto this special board shape
so that everything would fit with enough room to route the traces.

After arranging the components, I routed the traces to connect the pads according to the schematic while 
consideing how the traces would fit around the star's shape without creating uneccesary overlaps or making 
the layout too complicated. 

Finally, after the main layout was done, I added some personal touches to make the PCB my own. I added the 
Deltarune logo, and my initials to the F.Silkscreen layer, which printed the graphics onto the front of the
board.

<img width="407" height="350" alt="image" src="https://github.com/user-attachments/assets/5307a7ad-fdbd-4574-a11b-9a30451945d2" />


## Code and Firmware
For the code and firmware, I started with the existing base code and made a few tweaks to give the project
more personality. I added a sparkle trail effect to make the animations more interesting, along with 
my own custom bitmap pet.

The bitmap pet was a fun way to personalize the project beyong just the physical design. It also 
gave me an opportunity to experiment with how graphics are represented in code. I wanted the software to 
complement the pysical design, so adding custom visuals was a great way to make the finished Starbie
feel unique to me.

<img width="778" height="336" alt="image" src="https://github.com/user-attachments/assets/2725b172-63ad-4cc7-bb97-32b7d4c790d4" />


# What I learned
Starbie was my first experience designing a PCB, so almost every stage involved learning something new.
I had worked with breadboards before but designing a custom board came with new challenges like
thinking about how the components would fit together, or how to route the panels.

<img width="510" height="356" alt="image" src="https://github.com/user-attachments/assets/655e9223-aed6-49b6-9fd3-169dbb00e5ef" />





