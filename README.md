[linux final readme for d2l.md](https://github.com/user-attachments/files/23978832/linux.final.readme.for.d2l.md)
This project is a simple distance sensor that turns on a light. You will need a distance sensor, 3 resistors, 1 led, and many wires.

First step is following this :[https://gpiozero.readthedocs.io/en/stable/recipes.html\#distance-sensor](https://gpiozero.readthedocs.io/en/stable/recipes.html#distance-sensor)  
This shows how to wire the distance sensor. If the sensor smells like it's burning, then it's wired wrong. Try switching the 1st and 4th wires on the distance sensor.  
 ![20251202_122734](https://github.com/user-attachments/assets/22148847-79e4-4a48-bd54-c137113646ed)
![20251202_122732](https://github.com/user-attachments/assets/570d2f60-dcf4-4eee-b7d9-e9b41605a4fd)

To test if everything is working copy this code.

\`\` **from** **gpiozero** **import** DistanceSensor  
**from** **time** **import** sleep

sensor \= DistanceSensor(23, 24)

**while** **True**:  
    print('Distance to nearest object is', sensor.distance, 'm')  
    sleep(1)  
\`\`  
Typically, i have to switch 23 and 24\.

Step two is connecting the led, in the picture you see one wire connected to the pi, the led, a resistor, and a wire to ground on the breadboard, in the picture the led is on the gpio13 pin.  
 ![20251202_121504](https://github.com/user-attachments/assets/b25455d6-a3ad-461d-93f0-220fcce750e7)

Finally if nothing smells like burning you run the new code  
\`\`from gpiozero import DistanceSensor, LED  
from time import sleep

sensor \= DistanceSensor(24, 23\)  
led \= LED(13)

while True:  
    print('Distance to nearest object is', sensor.distance, 'm')

    if (sensor.distance \<= .5):  
       led.on()  
       sleep(1)  
    else:  
        led.off()  
\`\`  
The sensor distance can be changed.  
This turns on  a led when it senses something in range, and turns it off when not in range.  
