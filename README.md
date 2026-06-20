# Image-processing-and-Stateflow-driven-path-tracking-algorithm
A line-following application for a drone competition organized by MathWorks, under the specified conditions
Development of a line-following algorithm for the MathWorks Minidrone Competition. The simulation was performed using Simulink and MATLAB. In the given environment, the line to be followed is red, and there is a circle at the end of the red line for landing. The camera on the drone is used to detect the lines and the circle. The project consists of two stages: image processing and path-following algorithm:
1. Image processing:
2. To effectively isolate the red channel, a specific matrix operation is applied to each pixel vector P = [R, G, B]. While the non-target color channels are suppressed, the red spectrum is enhanced using the following formula: I= R- G/2 -B/2.
3. This thresholded matrix is processed using a specific threshold value. The pixels are converted into a binary matrix—where 1 represents the path and 0 represents the background—to remove noise.
