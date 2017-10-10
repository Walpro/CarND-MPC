# **CarND-MPC-Project** 

## Writeup
---

**Model Predective Control Project**
* This repository conatins the implementation of a MPC controller for steering angle and speed in c++.
* This project is part Udacity self driving car nanodegree.

### 1. Model

In this project a kinematic Model is used to model the vehicle, the model consists of the following states:

* Vehicle x position(xt)
* Vehicle y position(yt)
* Vehicle angle orientation(ψ​t)
* Vehicle speed(vt)

The state incorporates also the distance of vehicle from trajectory and the difference of vehicle orientation and trajectory orientation.

To next state is computed as follows:
* x​t+1​​ = x​t​​+v​t​​∗cos(ψ​t​​)∗dt
* y​t+1​​ = y​t​​+v​t​​∗sin(ψ​t​​)∗dt
* ψ​t+1 ​​= ψ​t​​+​vt/L​f​​​​​​​​∗δ∗dt
* v​t+1 ​​= v​t​​+a​t​​∗dt

To control the car two actuators are used, the throttle for vehicle speed control and the steering angle.

### 2. Timestamp

The timestamp lenght is choosen experementally, I tried at first the value of 20 but the computations was intensive and the car get's off the road due to predecting too far in the future, using a lower value of 10 with an elapsed duration between timesteps of 0.05 showed better results.

###3 . Latency

To deal with latency the state of the car is updated 100ms in the future before it is feeded to the MPC optimizer.
By doing that the MPC was able to predict the optimle controls that considers the latency of control actions.



