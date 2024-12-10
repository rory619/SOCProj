---
layout: home
title: FPGA VGA Driver Project
tags: fpga vga verilog
categories: demo
---

Introduction: My name is Rory O Loughlin and this is my 3rd year SOC project that I made and coded and I have made a unique image using vivado to generate to the screen. I have created an alteration between a sun and a moon that changes every sesond from day to night. This involved changing the VGAColourStripes code to create a unique image. 

I am adding a test sentence here at 13:24 on 03/12/24.

## **Template VGA Design**
### **Project Set-Up**
I am using a VGA Colour stripes file in VIVADO to change the picture that is being generated onto the screen. 
Summarise the project set-up and design flow. Include a screenshot of your own set-up, for example see the image of my Project Summary window below. Guideline 1 short paragraph.
![Screenshot 2024-12-10 130838](https://github.com/user-attachments/assets/dd7d259b-340a-4bc8-baed-45240e5426dd)

### **Template Code**
For the original colour stripes file, the module generates vertical stripes based on the row number on a VGA screen. Each stripe has a different color, cycling through black, blue, green, cyan, red, magenta, yellow, and white. The logic checks the row position (row) and determines the color to display for that row. The output colors are updated based on the clock, with asynchronous reset behavior to ensure the RGB values are initially set to black. It will display several different stripes to the screen.
Outline the structure and design of the Verilog code templates you were given. What do they do? Include reference to how a VGA interface works. Guideline: 2/3 short paragraphs, consider including screenshot(s).
This is the waveform generated from the behavioural simulation after running simulation:

![behavioural simulation](https://github.com/user-attachments/assets/b9391c8d-2ee5-4445-bd1a-e67f25fd5e9b)

VGA Controller Module: This module generates the horizontal (hsync) and vertical (vsync) synchronization signals for the VGA display. It also produces the pixel_x and pixel_y signals to track the current pixel’s position on the screen. The horizontal sync pulse occurs every 800 pixels (for a 640x480 VGA resolution), and vertical sync happens every 525 lines. These signals are essential for properly aligning the display’s pixels.

Pixel Generator Module: This module assigns RGB values for each pixel. It determines what color should be displayed at the given pixel position. For example, if pixel_x and pixel_y fall within the range of a specific image or color band, it outputs the corresponding RGB values. This module may contains a more complex image pattern generator (e.g., sun/moon) based on time or other conditions.

Testbench: The testbench is used to simulate the behavior of the VGA controller and pixel generator. It provides a clock signal and resets the design. The testbench generates the expected row and column values to test the correctness of the RGB output and sync signals. It can also include timing checks to verify that the sync pulses occur at the correct intervals.
### **Simulation**
Explain the simulation process. Reference any important details, include a well-selected screenshot of the simulation. Guideline: 1/2 short paragraphs.
 The testbench generates clock signals, applies reset conditions, and provides input signals such as row and column values for the VGA display. The simulator runs the design to model its functionality, with the testbench acting as a stimulus to simulate different input conditions (e.g., pixel coordinates, reset). After simulation, the output is viewed through waveform viewers, where the values of signals like hsync, vsync, and RGB outputs can be viewed for correctness.

 Some details to consider include ensuring the clock frequency matches the design’s timing requirements (e.g., for VGA, around 25 MHz), and managing timing of the testbench to cover all edge cases, such as reset behavior, synchronization pulse generation, and pixel color changes. By analyzing the waveform output, you can verify that the design generates the expected pixel colors and sync pulses, ensuring it will work correctly when synthesized onto the FPGA.
### **Synthesis**
Describe the synthesis and implementation processes. Consider including 1/2 useful screenshot(s). Guideline: 1/2 short paragraphs.
The synthesis process in Vivado translates the Verilog design into a gate-level representation, optimizing the design for the target FPGA. This step involves mapping the high-level Verilog code into logical elements such as LUTs, flip-flops, and other resources available in the FPGA. During synthesis, Vivado checks for any syntax or logical errors and provides an estimate of the design’s resource utilization, such as the number of LUTs, registers, and I/O pins. This is the synthesis report that I recieved after running synthesis:

![synthesis report](https://github.com/user-attachments/assets/356f5729-3b29-4139-92d3-01e9571c5e84)

The implementation process follows synthesis and involves placing the logic elements into specific locations on the FPGA and routing the connections between them. Vivado generates the final layout of the design, ensuring timing constraints (like setup and hold times) are met. Implementation also includes bitstream generation, which produces the configuration file that will program the FPGA. Once the bitstream is generated, the FPGA can be programmed, and the design can be tested on actual hardware.
This is a picture of the circuit that my code created:

![implemented design](https://github.com/user-attachments/assets/88f61e60-6fd3-43d4-8e8b-abfe0495cebe)
### **Demonstration**
Perhaps add a picture of your demo. Guideline: 1/2 sentences.

## **My VGA Design Edit**
My idea was to create a checkered flag, but I got as far as changing the stripes to horizontal, then I decided to change it to create two alterating images of the sun and the moon that changes every second. I started by making just the sun, but at this stage I needed to research to find out more information to incorporate the rotation between the 2 images. 
Introduce your own design idea. Consider how complex/achievabble this might be or otherwise. Reference any research you do online (use hyperlinks).
### **Code Adaptation**
I have adapted the code by creating a series of if statements to generate the alternating images. I used ChatGPT to give me a better idea of what direction I had to go to get my vision working. I asked it how I would alter the code I already have to generate an alterating image and the sun and the moon and I recieved the neccesary information in order to get it working. Now I have 2 different images that change every second to the sun with a grass floor and the moon with stars surrounding it I have the sun and moon dimensions in paramaters and I used reg to set a counter to shift over a period of time, for the position of the sun and the moon and to set a flag for day and night. Im using  if (day_night == 1'b1) for declaring sun logic and  if (day_night == 1'b0) begin for moon logic.
Briefly show how you changed the template code to display a different image. Demonstrate your understanding. Guideline: 1-2 short paragraphs.

### **Simulation**
To simulate the design in Vivado, I would first open the Verilog file (ColourStripes.v). Then, I would use the testbench module that generates clock signals and applies various reset and row/column values to the design. The testbench would include a clock generation process and assertions to check that the correct RGB values are produced for specific row and column inputs. I would set up a simulation environment using the "Simulation" settings in Vivado, running it in either behavioral or RTL simulation mode.
Show how you simulated your own design. Are there any things to note? Demonstrate your understanding. Add a screenshot. Guideline: 1-2 short paragraphs.
### **Synthesis**
Describe the synthesis & implementation outputs for your design, are there any differences to that of the original design? Guideline 1-2 short paragraphs.
When synthesizing and implementing the original ColourStripes design, Vivado would generate a bitstream that configures the FPGA to output colored stripes based on row and column positions. The synthesis output includes resource usage estimates (such as LUTs, flip-flops, and I/Os), while implementation provides the placement and routing of these resources, ultimately creating the bitstream file used to program the FPGA.

After re-creating the VGAColourStripes to display the images of the sun and the moon every second the complexity has increased.  Instead of a simple row-based color assignment, additional logic would be needed to handle the switching of image patterns over time. This could involve a counter to track time (1-second intervals), and a more complex pixel-by-pixel pattern generator for each image. As a result, the synthesis output would likely show an increase in resource usage, particularly in terms of logic elements and possibly memory usage. The implementation would also involve more routing due to the additional control logic, possibly impacting timing constraints and the overall design's performance.



Below is the synthesised design that was generated from my code:
![synthesised design](https://github.com/user-attachments/assets/0968074f-6f53-44ba-8daf-710cebb1f3dc)

This is a more zoomed in version of the synthesised design:
![circuit zoomed in](https://github.com/user-attachments/assets/7b0156bd-66b8-4140-9513-3c97da151c64)



### **Demonstration**
This is my working image that I made of the sun and the moon: It changes every second between day and night displaying the sun and the moon.
If you get your own 
design working on the Basys3 board, take a picture! Guideline: 1-2 sentences.
![1733846094350](https://github.com/user-attachments/assets/bf1b10af-68d6-403c-ac26-1604c49c3d60)
![1733846094352](https://github.com/user-attachments/assets/1d0e0fcf-3f03-45e3-a6ca-9641ea46f727)


## **More Markdown Basics**
This is a paragraph. Add an empty line to start a new paragraph.

Font can be emphasised as 
alic* or **Bold**.

Code can be highlighted by using `backticks`.

Hyperlinks look like this: [GitHub Help](https://help.github.com/).

A bullet list can be rendered as follows:
- vectors
- algorithms
- iterators

Images can be added by uploading them to the repository in a /docs/assets/images folder, and then rendering using HTML via githubusercontent.com as shown in the example below.

<img src="https://raw.githubusercontent.com/melgineer/fpga-vga-verilog/main/docs/assets/images/VGAPrjSrcs.png">
