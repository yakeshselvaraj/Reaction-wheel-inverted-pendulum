# Reaction-wheel-inverted-pendulum
 inverted pendulum, which will be stabilized using a reaction wheel mounted at the end of the pendulum. Closed loop control of pendulum speed, pendulum position, reaction wheel speed, and reaction wheel position will be implemented through the use of a linear quadratic regulator in combination with a swing-up procedure. The pendulum will be mounted on the linear rail  and a joystick will be used to control movement of the linear rail. To demonstrate that there is no connection between the pendulum control and linear rail movement, a separate microcontroller will be used to drive the linear rail.
 
 
 
 HARDWARE SETUP
	
 The base of the system is a stepper motor driven linear stage. The stage consists of a v-slot rail with a Nema 23 stepper motor mounted on one end utilizing a belt drive to move the pendulum base along the rail. The stepper is controlled manually using push button switches, an Arduino Uno, and a stepper driver in an open loop control configuration
