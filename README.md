# 3DMapper
## Made by Zaeem Ghauri

### What is this?
This is an embedded systems project I worked on as part of my ENGINEER 2DX4 course at McMaster University during my 2nd year. It was my first experience with microntrollers and embedded systems, and at first it was confusing and overwhelming, but I got the hang of it eventually. It was developed mostly in C and Python- C was used for the microcontroller itself, and Python for the data processing. The actual project features a lot more files but I have decided to exclude them so that I don't violate the University's academic dishonesty policy. I have also left out the 3D modelling part of the Python file for that very reason. Nonetheless, here is the code for the 3DMapper, a device that maps the user's surrounding in 3D. 

### How does it work?
The device uses the MSP432E401Y microcontroller interfaced with the VL531X time of flight (ToF) sensor, the ULN2003 stepper motor, and the user’s PC. The ToF sensor sends measurements to the microcontroller via I2C communication. These measurements are then passed on to the user's PC via UART communication where a Python script processes the data. The ToF sensor measures the distance between itself and a point on an object by emitting a light signal and calculating the time that it takes for the signal to reflect back. This distance value is used to find the x and y components of the point in 2D space. The ToF sensor is mounted on top of the stepper motor to complete a full rotation during which numerous measurements are taken. The z-axis (distance the device is moved forward for each scan) is added automatically to complete the x,y,z coordinates. The result is a 2D plane filled with points outlining the user's surroundings. These points are then connected with one another to create a 3D mesh of the area.

### How do I use it?

1. Connect the microcontroller to your PC with a USB cable.

2. Run the Python script and then restart the microcontroller. You should see a boot-up message followed by a prompt to start the scan in the Python console. 

3. Start the scan by pressing the button on the breadboard. You should see messages that provide the details of each measurement taken:
   "This is scan number ..., measurement ..., distance measured = ...mm"
   Make sure the ToF sensor has rotated back to its original position.

4. Move the device forward as far as the 'displacement' variable in the Python code has been set (this can be changed to your preference).

5. Repeat steps 3 and 4 until the number of scans have been fullfilled and the serial port is closed (get a message in the console stating "Closing: COM"). The Python script 
   should then automatically open up the 3D render of your surroundings.
   *NOTE: the 3D rendering has been taken out of the Python script so unless you have the full script, a render will not automatically open and instead the script will just end.* 

