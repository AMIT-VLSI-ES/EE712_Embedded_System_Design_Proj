# EE712_Embedded_System_Design_Proj
Vector-Parallel Graphics Accelerator Project report EE-712
# 1 Motivation
  This project implements a 2D graphics accelerator with the rasterization
being done on the PL side. Rasterization is a process in the
graphics rendering pipeline where the algorithm decides whether a
pixel is inside a triangle. This is one of the fundamental steps for
any graphic rendering pipeline. The rasterization algorithm is very
computation-intensive and repetitive, making it a good candidate to
vectorize and parallelize the operation. The rasterization algorithm
is applied to the entire vector dataset, in our case, 307200 pixels.
This rasterization is done in parallel on the PL side, freeing up the
processor resources.

# 2 Functional Requirements

  The PS side should run a bare metal program that takes the triangle
coordinates from a file and loads them into the Rasterizer module.
The Rasterizer should be capable of the following:
•   Support AXI-Lite read and write for communicating with the
PS.
• Store triangle coordinates in a buffer whose depth is a parametric
value for scalability.
• The screen size should be parametric to accommodate different
displays.
• Read the triangle coordinates in a loop and rasterize for all
pixel values.
• Rasterize for all the pixels in parallel and output pixels in AXIStream
format.
The output of the Rasterizer should be fed into the Xilinx AXI
stream to the video out IP. AXI-Stream will interface with a Digilent
RGB to DVI Encoder IP. This IP directly interfaces with the TDMS
ports of the HDMI interface. The AXI-Stream video out IP core is
controlled by a Xilinx Video Timing Controller IP.
