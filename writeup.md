# PID Control Project
## Goals
In this project you'll revisit the lake race track from the Behavioral Cloning Project. This time, however, you'll implement a PID controller in C++ to maneuver the vehicle around the track!

The simulator will provide you the cross track error (CTE) and the velocity (mph) in order to compute the appropriate steering angle.


### I. Basic Build Instruction
The aim of the PID controller is to output the steering angle based on the cross track error(CTE). 
1. The Porportional term, scales the cte into steering actions. With a large number it will lead the system unstable( growing osillations).

2. The Derivative term defines the difference between current and recent error. It can determines the  transient response (i.e. overshoot, settling time, ...), as well as the stability of the system. 

3. The Integral term reacts the accumulated error. It can eliminate the steady-state error, since it adds a pole at origin in the frequency domain, and increases the system type by 1.

### II. Tuning procedures
For a control engineer, a formal way to design a PID controller is based on the transfer function of the system, and use suitable methods i.e. root locus, Bode plot to determine those parameters. Here, since the dynamics of our car is unknown, the P, I, D parameters will be find by experiments. 

Often time, PD controller will design first, since it determines the transient response of our system. For the PI controller, it can only change the steady-state error(drift in our case), and we will tune it at the end.

For PID controller design without knowing the dyanmics of the system, there is a very well known method named Ziegler-Nichols rule. The procedures are given as follow:
1. Tune the Porportional term, increase Kp until it first exhibits sustained oscillations(marginally stable).
Kp = 0.15.
2. Determine the Derivative term based on the period of this oscillation. Kd = 9
3. Give a small value of integral term to get rid of the drift. Ki = 0.002.

### III. Test
The PID controller design above perform as expected with given speed.