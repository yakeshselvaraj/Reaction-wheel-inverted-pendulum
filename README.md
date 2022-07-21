# Reaction-wheel-inverted-pendulum
 Inverted pendulum, which will be stabilized using a reaction wheel mounted at the end of the pendulum. Closed loop control of pendulum speed, pendulum position, reaction wheel speed, and reaction wheel position will be implemented through the use of a linear quadratic regulator in combination with a swing-up procedure. The pendulum will be mounted on the linear rail  and a joystick will be used to control movement of the linear rail. To demonstrate that there is no connection between the pendulum control and linear rail movement, a separate microcontroller will be used to drive the linear rail.
 
 
 
 HARDWARE SETUP
	
 *Stepper motor 
 *Linear stage
 *TB6600 Stepper Driver 
 *12V power supply
 *Pendulum
 
 
 
 
 CONTROL STRATEGY
 
Stepper Motor Control
The stepper motor and linear stage are in place to serve as a disturbance input to the pendulum control system. Since the stage was already on-hand from a previous PROJECT, the entire pendulum assembly was mounted on the rail. Once the pendulum is stabilized in its vertical position, the stepper motor can be driven forward or backward, adding an external disturbance into the system.
The stepper is driven using an Arduino Uno, and a TB6600 Stepper Driver. Direction of the stepper is commanded by two push buttons. 12V power is supplied by one of the outputs on a DC power supply.
Pendulum Control
The pendulum control system has two primary operation modes, stabilize and swing-up. If the pendulum arm is within 0.1*π radians from vertical, then the control system operates in stabilize mode. In this mode a linear quadratic regulator (LQR) is used to compute a motor torque setpoint based on inputs of pendulum arm angle, pendulum arm angular velocity, flywheel angle, and flywheel angular velocity. The motor torque setpoint is then input to the motor commutation controller, which computes the required motor phase voltages to obtain the requested torque based on motor phase angle, motor angular velocity, and motor velocity constant Kv. In addition to these two controllers, an automatic setpoint adjustment PI controller is used. This controller uses the wheel angular velocity control deviation to dynamically adjust the pendulum arm angle setpoint to find the optimal vertical balancing position.

If the pendulum is outside of the 0.1*π radians stabilization range, then the control system operates in swing-up mode. In this mode the pendulum arm angular velocity is used to determine which direction the pendulum arm is swinging towards. The motor torque setpoint is then adjusted to put energy into the system, driving the pendulum oscillation higher and higher with each swing until the stabilization range is reached, where the stabilize mode controls take over. Figure 8 below shows a control block diagram for the pendulum.

