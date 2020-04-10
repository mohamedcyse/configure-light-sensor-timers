#The fast and reliable reaction of automotive functions is assured by software and Ecus.Moreover
former mechanical functions were replaced by software , Ecus , sensors and actuators.

#The requirements of the ECUs in today's automobiles are the following: 
-Reliable under rough and changing ambient conditions like temperature, humidity and vibration.
-High demands to the dependability and availability.
-High demands to the security. 

#The evaluation board from Raisonance serves as development and testing platform
 for the SPC560P controller from STMicroelectronics.

-Eight red transistor-driven LEDs (D0 – D7) that light up when the command is low.
Current is supplied by the power supply (9V or USB).

-Eight jumpers enabling the independent use of each LED. The use of an LED is 
enabled when the corresponding jumper is plugged in.

-Two-position jumper to choose the polarity of the BT6 push button. 

-Two push buttons and four switches. When the switches are on or the buttons pressed, 
the corresponding signal is tied to the ground (except for BT6 which depends on the
chosen polarity).

#Four-position analog connector which includes:
-Two analog inputs that can be connected directly to the ADC input pins of the 
microcontroller. 
-Analog output resulting from the integration of a PWM output.
-The integration is done with a simple RC filter with a characteristic time of 100ms.
-Ground connection. 
-Potentiometer, that can be connected directly to the ADC input pins of the microcontroller.
-Temperature sensor, that can be connected directly to the ADC input pins of the 
microcontroller.
-The output voltage of this sensor is given by the formula V=0.01(T+1).
-Buzzer that can be connected to the PWM microcontroller output through the PWM/BUZ jumper.


#Communication Area:
-Three-position connector for I²C communication.
-RS-232 connector.
-Four-position connector for SPI communication.


#Initial Setup:
-To implement functions on the ECU, the “Raisonance Ride7” IDE will be used.
-To flash code to the board “Rflasher7” is used.
-The compiler must be started by opening “WindRiver -> Development Shell” in the
start menu or on the desktop.
-Then it is necessary to enter the command “ride7” in the development shell to start the IDE.  
-It is mandatory to do this first. Otherwise the code will not be compiled. 
-The flashing program can be found under “Raisonance tools -> Ride7 -> RFlasher7” in
the start menu.


#First part:
-Configure the pins as general purpose output for the LEDs.
-Therefore it is necessary to refer to the additional document 
(“pin_muxing.pdf”) which is provided.


#Second part:
-The light sensor (photoconductive cell) is used in automobiles to automatically turn
on/off the head lights.  
-The implementation shows the automatic activation of actuators regarding sensor data.
-This part concerns with displaying the value of the light sensor data through LEDs.
-The controller pin, which is mapped to the ADC module, has to be configured for analog input.
-The function “showData( value )”  contains the code for the different value levels. 
-The highest value of the sensor all LEDs should be switched on.
-This part also concerns with The usage of the potentiometer provided on the board.
-The digitally converted values of the ADC unit lie between 0 – 1024 (10bits).



#Third part: 
-In this part digital inputs and timer-functionality will be used. 
-A button can be configured as input by writing “0x0100” to the corresponding PCR register. 
-A button press or a switch on action results in a low signal (“0”) on the pin. 
-The PIT timer channels 0 and 1 have been configured. 
-The timers can be started by calling the function “PIT_StartTimer( int timerChannel )”.
-The timers can be stopped by calling the function “PIT_StopTimer( int timerChannel )” .

 


 

 
  
  