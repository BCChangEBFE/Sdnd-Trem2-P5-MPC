# CarND-Controls-MPC
Self-Driving Car Engineer Nanodegree Program
This is my solution for udacity project hosted at https://github.com/udacity/CarND-MPC-Project
---

##The Model

Student describes their model in detail. This includes the state, actuators and update equations.

##Timestep Length and Elapsed Duration (N & dt)

N=25 and dt = 0.1 is chosed.
Because we are providing the needed 100 millisecond latency prediction hence dt = 0.1 seemds like a logical choice. 
I have tried N = 15,20,25,30,35,40: 
  It seems that when N is too large, the fitted polynomial would sometimes have very large coefficients that provides a path not ideal to follow.
  Witht the lower N values, the vehicle seem unable to see into the future and would sometimes need to try and make very sharp turns which is not always done gracefully.

##Polynomial Fitting and MPC Preprocessing

A 3rd degree Polynomial is fitted to waypoints. The waypoints here are preprocessed so the coordinates are of car space instead of global coordinates.

#Model Predictive Control with Latency

Latency is dealt with by feeding a state that is 100 millisecond into the future. The future state here is estimated by 
 px = v * dt
 psi = -v * steer_angle * dt / Lf;

