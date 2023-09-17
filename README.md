# CEN-598-Embedded-Machine-Learning
EML Projects
LED_BLE_SWITCH Project : 
----------------------------------------------------------------------------------------------------------------------------------------------------------------
Introduction: 
--------------
The BMI/CEN 598 Mini Project 1 involved the development of a state machine using the Arduino Nano BLE Sense development board. This state machine utilizes the board's inbuilt RGB LED connected to pins 22,23,24 respectively, to simulate the behavior of a push button switch since there is on-board switch in the Arduino Nano BLE Sense board, we are implementing a soft switch using nRF connect Mobile app using BLE protocol for transition between different states. The primary goal of this project was to create a functional state machine that responds to user input from the BLE application and changes LED colors accordingly. This report provides an overview of the project, its implementation, challenges faced, and lessons learned.

Project Description:
-----------------------
The project requirements were as follows:
Utilize the Arduino Nano BLE Sense board with an inbuilt RGB LED connected to pins 22, 23, and 24.
Implement a state machine with the following states and transitions:
•	Initial state: 'Dark' (LED off or dark color)
•	Transition to 'Red' state upon pressing an onboard switch (SW).
•	Transition from 'Red' to 'Dark' state after a 5-second delay.
•	Transition from 'Red' to 'Blue' state upon pressing SW in our case on receiving input from BLE app.
•	Transition from 'Blue' to 'Red' state after a 4-second delay.
•	Transition from 'Blue' to 'Green' state upon pressing SW i.e., receiving input from BLE app.
•	Transition from 'Green' to 'Blue' state after a 3-second delay.
•	Transition from 'Green' to 'Dark' state upon pressing SW i.e., receiving input from BLE app.
One possible method to implement the switch was through Bluetooth communication with a phone using third party app like LightBLue or nRF connect mobile app, in our project we have utilized the nRF connect Mobile app which allows the user to send commands to indicate a switch press.
Code Implementation: 
We implemented the state machine using C source code and used the Arduino IDE adhering to the project requirements. To summarize our implementation:
•	We utilized the inbuilt RGB LED on the Arduino Nano BLE Sense board to represent the different states as follows: 
o	DARK_STATE: This state represented LEDs when all are turned off
o	RED_STATE: This state represents only RED LED is turned on.
o	BLUE_STATE: This state represents only Blue LED is turned on.
o	GREEN_STATE: This state represents only Green LED is turned on.

•	We implemented logic to handle state transitions based on BLE input or timer delays.

STATES	BLE input Values	Timer Delays
DARK_STATE	0x00	N/A
RED_STATE	0x01	5 seconds
BLUE_STATE	0x02	4 seconds
GREEN_STATE	0x03	3 seconds

•	We implemented the conditions such that if switch input is not received between given intervals, the transition will happen as per requirements.
•	If we receive the switch input, it will be handled accordingly.
•	We set up Bluetooth communication for simulating the switch input from a connected device in Android phone -nRF Connect Mobile application downloaded from play store.
IMPORTANT NOTE: Since the timing intervals were too short to manually send the commands from BLE nRF connect Mobile app to our BLE peripheral (BLE Nano Sense 33 Board), we increased the timing intervals such as 10 seconds,8 seconds,7 seconds for our demo purpose in the video to illustrate the complete logic.

Observation and Challenges: 
----------------------------
During the project, we encountered several challenges:
•	Bluetooth communication setup was challenging, and we had to spend additional time ensuring a stable connection between the Arduino and the controlling device. Sometimes, at first instance the device does not connect which might be the mobile app issue. 
•	Debugging the code to ensure smooth transitions between states and accurate timing was a critical task.
•	Maintaining code clarity while handling multiple states and transitions required careful planning and commenting.
•	Managing and coming out of a way to manually implement the switch with the given delay as 5s,4s,3s was challenging, thus we had to find a work out for the same so that the logic remains same but we can clearly illustrate the process.

Lessons Learned:
-------------------
Through this project, we gained valuable insights into embedded systems development, state machines, and Bluetooth communication. Some key takeaways include:
•	Understanding the importance of well-commented code for collaboration and future reference.
•	Enhancing problem-solving skills by debugging and resolving issues.
•	Developing proficiency in handling hardware and software interactions in embedded systems.
•	Understanding BLE concepts like BLE central/peripheral roles and functions.
•	Read/write BLE data, BLE services, BLE characteristics, and practically using the knowledge.

Conclusion:
-------------
In conclusion, the BMI/CEN 598 Mini Project 1 provided a practical opportunity to implement a state machine using the Arduino Nano BLE Sense board and explore the BLE protocol. We successfully created a functioning state machine, adhering to project requirements. This project has enriched our knowledge of coding in Arduino and BLE, and we look forward to further challenges in this field.
