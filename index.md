---
layout: home
title: FPGA VGA Driver Project
tags: fpga vga verilog
categories: demo
---

Introduction: This is my 3rd year SOC project that I made and coded and I have made a unique image using vivado to generate to the screen. I have created an alteration between a sun and a moon that changes every sesond from day to night. This involved changing the VGAColourStripes code to create a unique image. 

I am adding a test sentence here at 13:24 on 03/12/24.

## **Template VGA Design**
### **Project Set-Up**
I am using a VGA Colour stripes file to change the picture that is being generated onto the screen
Summarise the project set-up and design flow. Include a screenshot of your own set-up, for example see the image of my Project Summary window below. Guideline 1 short paragraph.

<img src="https://raw.githubusercontent.com/melgineer/fpga-vga-verilog/main/docs/assets/images/VGAPrjSum.png">
### **Template Code**
For the original colour stripes file, the module generates vertical stripes based on the row number on a VGA screen. Each stripe has a different color, cycling through black, blue, green, cyan, red, magenta, yellow, and white. The logic checks the row position (row) and determines the color to display for that row. The output colors are updated based on the clock, with asynchronous reset behavior to ensure the RGB values are initially set to black.
Outline the structure and design of the Verilog code templates you were given. What do they do? Include reference to how a VGA interface works. Guideline: 2/3 short paragraphs, consider including screenshot(s).
### **Simulation**
Explain the simulation process. Reference any important details, include a well-selected screenshot of the simulation. Guideline: 1/2 short paragraphs.
### **Synthesis**
Describe the synthesis and implementation processes. Consider including 1/2 useful screenshot(s). Guideline: 1/2 short paragraphs.
### **Demonstration**
Perhaps add a picture of your demo. Guideline: 1/2 sentences.

## **My VGA Design Edit**
My idea was to create a checkered flag, but I got as far as changing the stripes to horizontal, then I decided to change it to create two alterating images of the sun and the moon that changes every second. I started by making just the sun, but at this stage I needed to research to find out more information to incorporate the rotation between the 2 images. 
Introduce your own design idea. Consider how complex/achievabble this might be or otherwise. Reference any research you do online (use hyperlinks).
### **Code Adaptation**
I have adapted the code by creating a series of if statements to generate the alternating images. I used ChatGPT to give me a better idea of what direction I hd to go to get my vision working. I aked it how I would alter the code I already have to generate an alterating image and the sun and the moon and I recieved the neccesary information in order to get it working.
Briefly show how you changed the template code to display a different image. Demonstrate your understanding. Guideline: 1-2 short paragraphs.
### **Simulation**
Show how you simulated your own design. Are there any things to note? Demonstrate your understanding. Add a screenshot. Guideline: 1-2 short paragraphs.
### **Synthesis**
Describe the synthesis & implementation outputs for your design, are there any differences to that of the original design? Guideline 1-2 short paragraphs.
### **Demonstration**
This is my working image that I made of the sun and the moon:
If you get your own design working on the Basys3 board, take a picture! Guideline: 1-2 sentences.

## **More Markdown Basics**
This is a paragraph. Add an empty line to start a new paragraph.

Font can be emphasised as *Italic* or **Bold**.

Code can be highlighted by using `backticks`.

Hyperlinks look like this: [GitHub Help](https://help.github.com/).

A bullet list can be rendered as follows:
- vectors
- algorithms
- iterators

Images can be added by uploading them to the repository in a /docs/assets/images folder, and then rendering using HTML via githubusercontent.com as shown in the example below.

<img src="https://raw.githubusercontent.com/melgineer/fpga-vga-verilog/main/docs/assets/images/VGAPrjSrcs.png">
