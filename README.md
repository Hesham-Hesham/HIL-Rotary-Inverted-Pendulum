# Introduction
This project involves the design and implementation of a rotary inverted pendulum system using Arduino and Simulink. The system consists of a motor with a built-in encoder and an incremental rotary encoder for measuring the angle of the pendulum. The controller for stabilizing the system is implemented using an LQR controller.
# Components 
* Arduino uno
* Incremental encoder 
* motor with built-in encoder 
* 12V Battery 2200 mah
* H-bridge L298N 2A
* Breadboard

## Dependencies
* When you work with the code and model you must include the repo in Matlab path
* Include the Encoder function 
* Run the motor parameter file in workspace 
# Steps 
1. Desgin the CAD model and assemble it
2. Parameter estimaton for the motor to get the motor coffecients
    1. Give the motor a $\pm 12V$  signal
    2. Collect of the $V$ and $\frac{rad}{sec}$ in an excel file 
    3. Import the reading in the Matlab
    4. Build a simulated model using simscape library as the following fig: ![image](https://user-images.githubusercontent.com/81301684/209942131-afcef869-960e-4c80-8c42-cd1c56d04ce5.png)
    5. Using the Parameter-Estimator app of simulink to match the parameters between simulated and real data
    
3. Get the gain of LQR by using the mathematical model built on Matlab 
4. Use the hardware in loop as follows :.![image](https://user-images.githubusercontent.com/81301684/209944508-2076fb9c-0b63-4146-bc5e-c6d17b49314f.png) <br>
5. You can use the gain button to enable or disable the analog pwm signal which activates and diactivates the motor



# State Space Model
<p align="center">
  <img src="https://user-images.githubusercontent.com/81301684/209886657-d23bd41b-5b84-484a-a1d1-812a3a5d1917.png" alt="image">
</p>

<p align="center">
  <img src="https://user-images.githubusercontent.com/81301684/209886802-cc0e819c-6bc1-4ef3-a986-052a14be2cd3.png" alt="image">
  <img src="https://user-images.githubusercontent.com/81301684/209886851-dfa734f8-b1f3-44b7-a5bd-99d6ea4dc7a6.png" alt="image2">
</p>

# Video

 [**Real-life video**](https://bit.ly/3Z7MPj8) 
<br />

https://user-images.githubusercontent.com/91581641/210287515-88685e6d-9f48-4c9a-a3e7-b1d94385d8b0.mp4



# Limitations
There is no swing up functionality in the current model. Additionally, there is some vibration present in the system. The system is able to work within an angle range of +20 to -20 degrees with the reference being the upright position, beyond which it will turn off until the pendulum is returned within this range.

# HIL Usage
To use the system, connect the electrical components to the Arduino board, connect Arduino board to a computer and open the Simulink model. Run the model and the system will start operating. The angle of the pendulum and the control signal can be monitored in the scope blocks in the model.

# Files

The repository includes the following files:
* MotorParameter.mat "which contain the esimtated motor parameter using parameter estimator tool"
* MotorModelEstimated.slx "A simulink file that contain a simscape model for the motor to be used in parameter estimation"
* model_inverted_rotary_pendulumV4.mlx "A live matlab script at which the model is applied ,in addition to be used in getting the response and LQR stability gains"
* RotaryInvertedPendulumHardwareInLoop.slx "A simulink Hardware in loop code for arduino uno that was programmed using simulink"
* Driver guide "folder that contain the simulink's arduino encoder driver in it" 

# Credits
This project was developed with the help of the following papers and videos:

* https://www.researchgate.net/publication/224178913_Modeling_and_control_of_a_rotary_inverted_pendulum_using_various_methods_comparative_assessment_and_result_analysis
* https://www.st.com/content/dam/AME/2019/Educational%20Curriculums/motor-control/Introduction_to_Integrated_Rotary_Inverted_Pendulum_v2.pdf4
* https://www.youtube.com/watch?v=ZGICyE1pDxo

