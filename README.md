# Automated-Dino-Game-using-Arduino
The dinosaur game appears in google chrome when you try to visit a website while
disconnected from the internet. Dino game is a simple infinite runner, which sees you jump
over cacti, and dodge underneath obstacles.
REQUIREMENTS AND CONNECTION: -
So for doing this we need an Arduino board, a LDR as sensor, a servo motor for pressing the
space bar and a resistor. The LDR is connected to the A0 pin of analog pins i.e. A0 pin acts as
the sensor pin. In case of servo motor, the power pin and the ground pin is connected to
the 5V pin and GND pin of the power pins and the sensor pin in connected to a PWM pin of
digital pins (Let’s say 3).

SYNTAX AND FUNCTIONS USED: -
1.#include<>
#include is used to include outside libraries in your sketch.
2. <Servo.h>
This library allows an Arduino board to control RC (hobby) servo motors.
3. setup()
This function is called at the beginning of the sketch. It is used for initializing
variables, pin modes etc.
3. loop()
Once the setup function is completed, the loop function is executed over and over
continuously.
4. pinMode(pin,mode)
This function is used to configure the pin specified to behave as input (INPUT) or
output(OUTPUT). 
5. write()
Writes binary data to the serial port.
6. if else
The if statement checks for a condition and executes the proceeding statement or
set of statements if the condition is 'true'. An else clause will be executed if the
condition in the if statement results in false.
7. attach()
Attach the Servo variable to a pin.

CODE DESCRIPTION: -
So the code for the game goes like thisFirst of all we need to include the servo library (as servo motor is used).
#include <Servo.h> //to include servo lib

Then we need to initialize and declare the variables. For the threshold value, 1st we have to
check for it by trial and error method and then put the value according to it.
int sensor_pin=A0; //initialisation of variables
int threshold_value=0; //change the value after finding the threshold value by trial and error method
int sensor_value; //declaration of variable
Servo s;

Then the attach() and pinMode functions were declared under void setup().
void setup() {
 s.attach(3); //pin 3 is attached to servo motor
 pinMode(A0,OUTPUT); //to set sensor_pin as output
}

Then under the void loop function the program was executed. The variable sensor_value
notes the output value of the sensor pin. If the sensor value is greater than the threshold 
value, it shows that there is an obstacle ahead and then the servo motor rotates by 90
degrees and the space bar is pressed i.e. the dinosaur jumps. Otherwise the dino keeps
running like that.
void loop() {
 sensor_value=analogRead(sensor_pin);//to get the sensor value

 if(sensor_value<=threshold_value){ //condition for servo motor to rotate 90 degree
 s.write(90);
 }
 else{ //otherwise it remains at 0 degree
 s.write(0);
 }
} 
