
## Rubric Points
###Student describes their model in detail. This includes the state, actuators and update equations.
**Answer:** 

1. State: The state of the Kinematic Model includes the 2d coordinates of the vehicle, angle of the car's orienrtarion, speed, cross track error and orientation angle error
2. Actuators: The actuators include the input of the vehicle, the steering angle delta and acceleration.
3. Equations: The update functions are used to calculate the current state based on the previous state and actuation from the previous step
  
###Student discusses the reasoning behind the chosen N (timestep length) and dt (elapsed duration between timesteps) values. Additionally the student details the previous values tried.
**Answer:** 
N*dt can only be couple seconds. dt needs to be small and T needs to be bigger
the latency is 100ms, so I chose 0.1s as dt, tried 15 and 10 as N, turns out 10 works best.
Tried N = 20, dt=0.05; N = 15, dt = 0.1,...

###A polynomial is fitted to waypoints. If the student preprocesses waypoints, the vehicle state, and/or actuators prior to the MPC procedure it is described.
**Answer:** 
The starting point of the vehicle may not be at the center of the road, so the way point data we get need to be processed to fit in the model in order to calculate the next state.
I transformed the waypoints based on the car's position and the waypoknts position, transformed the points to fit in the body, so the start point is 0,0 and with 0 orientation angle.


###The student implements Model Predictive Control that handles a 100 millisecond latency. Student provides details on how they deal with latency.
**Answer:** 
In MPC.cpp LINE 116-120, since dt I chose equals to the latency, I just need to delay the delta and acceleration for 1 step. The first and second step are the same.
