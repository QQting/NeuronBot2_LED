# NeuronBot_LED (Arduino Nano for example)

### Arduino IDE Setup and Sketch Upload (This step can be done on a laptop)

Click **Manage Libraries**  
<img src="https://github.com/jeremylu0601/NeuronBot_LED/blob/master/images/arduino_manage_library.png" width="800" height="400">


Install **Adafruit NeoPixel** for the Arduino Board.

<img src="https://github.com/jeremylu0601/NeuronBot_LED/blob/master/images/download_adafruit.png" width="600" height="200">


Set the **Board**, **Processor** and **Port** correctly.

<img src="https://github.com/jeremylu0601/NeuronBot_LED/blob/master/images/boardset.png" width="400" height="300"> 
<img src="https://github.com/jeremylu0601/NeuronBot_LED/blob/master/images/processorset.png" width="400" height="300"> 
<img src="https://github.com/jeremylu0601/NeuronBot_LED/blob/master/images/portset.png" width="400" height="300">

Open **Arduino_Nano.ino** in Arduino IDE and click **Verify** and **Upload** buttons to write the sketch into UNO.

<img src="https://github.com/jeremylu0601/NeuronBot_LED/blob/master/images/verify.png" width="300" height="200"> <img src="https://github.com/jeremylu0601/NeuronBot_LED/blob/master/images/upload.png" width="300" height="200">

### Hardware Setup (connect the Arduino board and NeuronBot)

Put the USB cable into the USB hub on NeuronBot.

Please find out to which port the Arduino board is connected, e.g., **/dev/ttyUSB0**.  


### Check the function

1. Install the dependence
    ```
    pip install pyserial
    ```
2. Execute the script
    ```
    python led_control.py --port /dev/ttyUSB0 --num 30
    # port : the port where the USB cable is, e.g., /dev/ttyUSB0.
    # num : the number of LED units on the strip
    ```
    <img src="https://github.com/jeremylu0601/NeuronBot_LED/blob/master/images/output_terminal.png" width="300" height="200">
    <img src="https://github.com/jeremylu0601/NeuronBot_LED/blob/master/demo_nano.gif" width="300" height="200">

### LED Define

The number of LED unit starts from 0 which is the unit closest to the wire.

<img src="https://github.com/jeremylu0601/NeuronBot_LED/blob/master/images/nano_led.png">

### Build your own LED function
Import the class **Strip** at the beginning 

For example,
```python
#!/usr/bin/env python
from led_control import Strip
if __name__ == '__main__':
    port='/dev/ttyUSB0' ## Port for the Arduino Board
    num=30 ## The number of LED units
    s=Strip(port,num) ## Initialize the strip.
    
    s.clear() ## Turn all LED units off.
    s.delay(1000) ## Wait 1000 ms to let the strip have enough time to execute the command.
                  ## Feel free to change the delay time.  
    s.setPixelColor(1,180,0,0) ## Define NO.1 LED unit be red with intensity 100.
                               ## We only define the LED unit, but the light is still off.
    s.show() ## Turn on strip.
    s.delay(1000)
    s.demo() ## Display all basic function in class Strip.
    s.close() ## Disconnect the serial port object.
```


