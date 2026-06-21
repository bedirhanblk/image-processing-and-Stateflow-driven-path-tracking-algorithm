# Image-processing-and-Stateflow-driven-path-tracking-algorithm
A line-following application for a drone competition organized by MathWorks, under the specified conditions
Development of a line-following algorithm for the MathWorks Minidrone Competition. The simulation was performed using Simulink and MATLAB. In the given environment, the line to be followed is red, and there is a circle at the end of the red line for landing. The camera on the drone is used to detect the lines and the circle. The project consists of two stages: Image Processing and Control System:

1. Image Processing: To effectively isolate the red channel, a specific matrix operation is applied to each pixel vector P = [R, G, B]. While the non-target color channels are suppressed, the red spectrum is enhanced using the following formula: I= R- G/2 -B/2. This thresholded matrix is processed using a specific threshold value. The pixels are converted into a binary matrix—where 1 represents the path and 0 represents the background—to remove noise. Virtual search beams are projected outward from the drone’s current position (the exact center of the camera matrix). These beams scan the binary environment between -15° and 195°, in 5° increments. The algorithm calculates the uninterrupted length of each beam until it exits the red boundary (0 pixels). A target direction is determined by weighting the calculated distances. The yaw angle is determined based on this direction. In addition, the distance directly in front of the drone (the length of the 90-degree beam), whether the drone is within a red zone, and whether it has detected a circle are continuously calculated. 
2. Control System: A state-flow-based approach is used here. The yaw angle error is fed into the PID block, and the desiredYaw output is obtained. The states in the state-flow are as follows:
"Bekle": For cases where the desired altitude has not been reached or a red zone cannot be found.
"yol_gozumu_dagliyor”: This is the main line-following algorithm and includes the “takip” state (for moving straight when the path ahead is clear enough), as well as the ‘yol_goster’ and “donuyoruz” states for use at corners.
For landing, it includes the “buraya_kadar_bekir” “pist_bulmaca” and “inelim” states.
An example line:

<img width="1132" height="697" alt="image" src="https://github.com/user-attachments/assets/a16a771b-b519-493f-b0a6-c345f18d82f2" />







https://github.com/user-attachments/assets/2a678804-f4ee-4488-9861-9fca56e3390a






https://github.com/user-attachments/assets/09022933-706c-4599-be24-42f2c7e4fa7d




https://github.com/user-attachments/assets/cbf46b4c-2130-4a5d-8be5-6d42876da91b






https://github.com/user-attachments/assets/683f1e79-6e06-463c-afe7-bafa4c773e2e




