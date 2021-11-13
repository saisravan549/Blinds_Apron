# Blinds_Apron

## Introduction

There are many problems blind people face ranging from walking freely in their house and doing all the activities to walking freely on the roads. Today, due to the advancement of technology, we have seen many software programs that help blind to operate electronic gadgets like mobiles and computers easily. We also see some advanced systems using deep learning and AI to help the blind walk and do almost all their activities with immense comfort.But the fact that most blind people are not used to get along with these advanced technical gadgets will always oppose these developments.It is not surprising to see the tradition followed by all the blind people to use a stick that could guide them in their daily life. It is true that this stick comes handy and helps the blind to detect all the things and events around them easily. But after all, it is operated by the blind himself and he can only use the stick to take help based on his understanding of surroundings. If the surroundings are hard to compile, it would become difficult for the blind.The proposed design in this paper can easily be worn my the blind and walk without much assistance.The proposed design uses VL53L1X Time-of-flight Lidar Sensors, Raspberry pi 4 , Pi camera, Arduino Nano and Google Vision Api services.The Lidar sensor which is based on Time of Flight technology, measures the distance to a target by emitting an energy source for illumination.It fires rapid pulses of laser light at a surface,anything up to 120,000 pulses a second.Time-of-Flight  measures the time taken for a wave pulse to reflect off an obstacle and return to the sensor. These sensors are placed on the system at specific positions.When the sensor at a specific position detect an object at a distance less than a certain threshold value,an indication is given to the blind at that respective position using vibration motor.In this way,the height and width of the obstacle can easily be judged based on the number of motors vibrating at different positions in the system .As a methodology of knowing the names of obstacles and objects around the blind, PICamera is used to capture pictures of the surroundings and  the captured image is sent to Google cloud vision services using the Vision Api in Raspberry pi 4 for detecting the objects in the image using the hybrid Convolutional Neural nets used by Google. Then the response JSON  is returned to Raspberry pi 4 which is then converted into speech for the blind to know about the objects around their surroundings using eSpeak library in Python .VL53L1X is also used in the system for pothole  and other uneven ground surface detection. 

## Design of the gadget

The proposed model is a smart wearable device which uses a total of 5 volts 3 amperes supply with rechargeable power unit.It has one micro HDMI output port coming from the raspberry pi 4 to configure the settings of raspberry pi by connecting to a monitor and a single charging port that is connected to rechargeable unit. The model uses VL53L1X time of flight  sensor to measure the time  it takes for the light beams emitting from the sensor to reflect and reach back the sensor again. This time value is then sent to the Arduino nano for processing and calculating the distance at which the light beam got reflected. A total of ten VL53L1X sensors are used in the proposed model attached to the different locations of the body and each sensor is provided with a separate arduino nano to increase the response time of the vibrating motors that are connected to each sensor. The vibrating motors start vibrating as soon as the arduino nano detetcts the distance of the reflecting point of the light beam less than 30 cm. These vibrations at different parts of the body can easily help the blind person to predict the size of the obstacle ahead without any manual effort. This feature makes the proposed design unique and stand out of line because no other design was able to help the blind person to detect and predict the height and size of the obstacles around him simultaneously  without manual effort. A single VL53L1X sensor is used to detect any uneven surfaces on the ground like potholes,speed breakers etc.This sensor along with the switching circuit which is used to switch off and on the sensors and RaspberryPi is controlled by Arduino mega. A GPU module is used to track the location of the blind person which is controlled by Raspberry pi. The GPU module sends the data to the Firebase using Raspberry pi and its inbuilt Wifi module and the caretakers can track the location of the blind people by importing the data from the firebase to a simple tracking application.Pi camera is used to capture the pictures intended by the blind person and the captured pictures are sent to Raspberry pi where the pictures are sent to Google Cloud using Vision API services and the picture is processed in the cloud to detect objects in the image and the results are sent back by the cloud pub/sub service to the raspberry pi. The results are then informed to the blind person using voice output which is in-build in Raspberry pi 4. The design also involves a security feature where the user of the product should enter a four digit pin by clicking the four sequential buttons that are provided at the side of the main body as shown in the FIG 3.These buttons are connected to Arduino mega and the functionalities of the Arduino mega such as switching on  the  sensors and Raspberry pi will only work if the right pin is entered by pressing the buttons. Once the right pin is entered, it makes a pin in the Arduino nano which is connected to that four buttons to go to HIGH state which is essential for the Arduino mega to perform its functionalities. This security feature is added mainly because to avoid unauthenticated users to operate the system.

![alt text](https://github.com/saisravan549/Blinds_Apron/blob/main/images/Screen%20Shot%202021-11-12%20at%207.13.59%20PM.png)

### VL53L1X  Time of Flight Sensors and obstacle detection

The selection of appropriate sensors depends on different factors such as Cost of the sensor, the type of obstacles to be detected, precision of measurement and detection range. Time of Flight sensors are more precise and quick in measuring the distances and also the detection range is high when compared to the traditional Ultrasonic sensors. They also weigh extremely less when compared to Ultrasonic Sensors which is really important because it adds to the comfort of the blind person. A total of ten such sensors are used in the proposed design located at different positions of the body. Each sensor weighs around 0.4 to 0.7 grams and will be operating at 15mA supply current.So the reason for selecting the VL53L1X time of flight distance sensors is mainly because of size and accuracy. These sensors are extremely small when compared to other distance measuring sensors like Ultrasonic and IR sensors. Also their accuracy is extremely precise which is definitely necessary since the product cannot compromise on accuracy of sensors as that could ultimately put the user in danger.


![alt text](https://github.com/saisravan549/Blinds_Apron/blob/main/images/Screen%20Shot%202021-11-12%20at%206.59.40%20PM.png)

The above image shows the comparison among three different distance measuring sensors. These comparisons conclude that VL53L1X Time of Flight sensor is much better when compared to Ultrasonic or IR sensor for the proposed design. The other feature of VL53L1X is that  additional components include Voltage regulator and Level shifter circuit.Voltage regulator will make the sensor work at 2.2V - 5.5V and the level shifter circuit is used to allow I2C communication.But I2C communication is not used in our current model because the need is insignificant. The range of these sensors is 4 meters and the working of these sensors is based on the time difference between the emission of light pulses and its return to the sensor.The Sensor also offers three distance modes: short, medium, and long. Long distance mode allows the user to measure the longest possible ranging distance of 4 m, but the maximum range will always be significantly affected by ambient light. Short distance mode is generally immune to ambient light, but the maximum ranging distance is mostly limited to 1.3 meters . The maximum sampling rate present in the  short distance mode is 50 Hz while the maximum sampling rate that is present in the  medium and long distance modes is 30 Hz. The advantage of having these different modes can be used in the product to set the working of the sensors based on the size of the environment the user is currently interacting.Even though the VL53L1X is not sensitive to external conditions, the main aim of the proposed design is to bring accuracy, comfort as well as fast responsiveness in the system.

Below diagram shows a situation where the blind can easily judge the height of different obstacles by wearing the system.Once the blind comes closer to an obstacle with a particular height, the vibrating motors on the system will vibrate at specific positions where the VL53L1X is exposed to the obstacle.

![alt text](https://github.com/saisravan549/Blinds_Apron/blob/main/images/Screen%20Shot%202021-11-12%20at%207.14.22%20PM.png)

### Potholes and  Uneven surfaces Detection

A VL53L1X sensor is placed at the abdomen level of the user. The sensor calculates the time difference between the light pulses hitting the ground surface and reflecting back to the sensor. This difference is sent to Arduino Mega. According to the instructions, Mega will either activate or deactivate Pothole indication.

### Algorithm Implementation:

Condition →True

Counter  → 0

Initial Value → Distance(Value read from the sensor)

Sleep for 2 seconds

While Condition is True:

         Reading Value -> Distance(Value read from the Sensor)
         
         If  Absolute(Initial Value - Reading Value) is less than 10 cm //Readings are consistent
         
                           If counter == 6  // To make sure that values are consistent for some time
                           
                                     Condition -> False
                                     
                           Else
                           
                                     Counter = Counter + 1
                                     
         Else    
         
               Initial Value  -> Reading Value   
               
               Counter  -> 0   
The above algorithm indicates that the sensor takes a couple of seconds to configure the initial reference value to a particular number through which the uneven surfaces are detected based on the difference between the reference value as mentioned in [10] and the subsequent values read by the sensor . This configuration is done based on the height of the user. This reference value will be constant until the user resets the system. This value is basically the  distance measured from the user's abdomen level to the ground at a particular angle, making a hypotenuse from the user’s abdomen to a point on the ground. This reference value is considered as ‘d’. 

![alt text](https://github.com/saisravan549/Blinds_Apron/blob/main/images/Screen%20Shot%202021-11-12%20at%207.15.58%20PM.png)

Now, if any Pithole  or slope is present ahead of the user, the value of this hypotenuse length measured by the sensor will either increase or go out of range.So if calculated_distance > d or calculated_distance = Out Of Range, then the proposed system will conclude that there is uneven road ahead and alert the user on the same. 

![alt text](https://github.com/saisravan549/Blinds_Apron/blob/main/images/Screen%20Shot%202021-11-12%20at%207.16.15%20PM.png)
![alt text](https://github.com/saisravan549/Blinds_Apron/blob/main/images/Screen%20Shot%202021-11-12%20at%207.16.25%20PM.png)
![alt text](https://github.com/saisravan549/Blinds_Apron/blob/main/images/Screen%20Shot%202021-11-12%20at%207.16.35%20PM.png)
These sensors are also used to detect objects with hollow bottoms like Tables and Chairs. For such objects, this hypotenuse length will fall drastically within seconds if the user tries to walk against these objects.The processing unit can identify such sudden drop and alert the user on the same. Since the initial threshold value is configured for the sensor, once it comes across an object above the ground level with some height, the distance measured by these sensors will fall down instantaneously. This drop can be detected by the microcontrollers and indicate the user regarding the event so that the user can take the measures to avoid the danger.

![alt text](https://github.com/saisravan549/Blinds_Apron/blob/main/images/Screen%20Shot%202021-11-12%20at%207.16.45%20PM.png)
![alt text](https://github.com/saisravan549/Blinds_Apron/blob/main/images/Screen%20Shot%202021-11-12%20at%207.16.56%20PM.png)
In FIG. 7, the sensor was encountered with a pothole within a time interval of 6 to 8 seconds thereby increasing the value of calculated distance from the user to the ground surface. In FIG. 8, the sensor was encountered with a dining table in front of the user. So, as soon as the user came close to the dining table,the distance measured kept dropping from 7th second to 10th second and later after walking away from the table, it restored back to the reference value. In FIG. 10, the user marched towards the downward steps and initially at 7th second the readings started to increase but at 9th second the readings of the sensor went out of range. 

![alt text](https://github.com/saisravan549/Blinds_Apron/blob/main/images/Screen%20Shot%202021-11-12%20at%207.17.46%20PM.png)

Pi camera captures pictures of the surroundings and outputs the image to raspberry pi. Raspberry pi will then send the image data to the cloud. In the cloud, the image is processed for object, features, landmark and logo detection using pre-trained models and the results are given back to the "text to speech conversion" module of the Raspberry pi.Then the results are recited for the blind to hear and judge the surroundings.
Once the image data is received by google cloud, it  uses Vision Api services to detect the objects , features etc in the image.Here Cloud Pub/Sub acts as a real-time messaging service which acts as an interface between the input image data and Vision Api. It is an Asynchronous messaging service that helps in decoupling the services that produce events from services that process the events.It simpy allows us to create one to many or many to one or even one to one publisher subscriber channels. In Vision APi services, we can use google pretrained prediction model trained with thousands of datasets and predict the objects, features and many other entities in the image. Auto Ml services is another way in which we can train our custom prediction model using our own datasets. After the prediction by the model, the results are sent to the raspberry pi for letting the user know about the object  captured with the help of pub/sub.. 
The most flexible features that google provide in Vision Api are:
Object detection
Feature detection
Landmark detection
Logo Detection
Optical Character Recognition
Google vision Api is known for its fast and accurate responses. Since blind people cannot afford delay in knowing the obstacles around them by using other GPU intensive deep learning techniques, Vision Api will be a better choice. 

### Vibrating motors

This  is a  DC vibration motor  used in  mobile phones. It generally requires a voltage supply of 3V to 5V with current around 125  mA. These types of  motors  can be programmed  to control its speed by using the Pulse Width Modulation(PWM) method although the default speed is used in the proposed system. The  diameter of the motor  is 0.5  cm and the thickness of the motor  is 2.5mm.

### 4 pin security lock

The inbuilt security system is provided with the help of the Arduino board. The circuit is designed in such a way that the user is provided with four different buttons along with a reset button, each button is assigned with numerical from 1 to 4. One terminal of the button switch is connected to its  respective digital pin in arduino and the other is grounded. When the switch is pressed the respective digital pin in the arduino turns low. Based on the pattern in which the pins are getting to lower states, the digital pin 7 will get its value. If the switches are pressed in correct order the output of digital pin 7 is high else the output is low. Once pin 7 is in its higher state ,that pin sends voltage signals to all the reading pins of the remaining microcontrollers which instructs them to follow the switching instructions from  the user. Once the user presses the reset button,  the system gets locked again. A simple LED is turned ON if the entered  pin is correct. In FIG .13, the apron system abstracts all the sensors that connect to pin 7 of Arduino Nano in a 4 pin security system. The setting access block abstracts all the switching operations that are performed on arduino system ones  pin 7 goes HIGH.

![alt image](https://github.com/saisravan549/Blinds_Apron/blob/main/images/Screen%20Shot%202021-11-12%20at%207.18.02%20PM.png)

![alt image](https://github.com/saisravan549/Blinds_Apron/blob/main/images/Screen%20Shot%202021-11-12%20at%207.18.26%20PM.png)

## Results and Discussions

After designing and implementing the technologies specified, Favourable results were obtained .The response from the cloud vision Api services was within 3 seconds of the request. Instead of processing the image for Object detection locally using custom Convolutional Neural Nets, which was taking nearly 15 seconds since it is GPU intensive work ,using the services of Google in the cloud to get quick results was a better option.

![alt image](https://github.com/saisravan549/Blinds_Apron/blob/main/images/Screen%20Shot%202021-11-12%20at%207.18.38%20PM.png)

The sensors also gave accurate measurements and immediate responses were given by vibrating motors and  voice signals based warning for  normal obstacles detection and potholes and other uneven surface detection respectively since each sensor is handled by separate Arduino nano .Since we cannot afford delay in detecting obstacles, Liar sensors were used instead of Ultrasonic sensors for detecting obstacles.Light waves are faster than sound waves and even the Lidar sensors are more accurate compared to Ultrasonic sensors.This design comes handy and can be carried anywhere. The total product weighs around 1.3kg which can easily be handled by any person. The system will run for 4 to 5 hours if used continuously and takes 3 to 4 hours to recharge.We can use 5 volts 3 amps supply to recharge the system even faster.The final prototype design was both tested on trained and untrained  blind persons.

![alt image](https://github.com/saisravan549/Blinds_Apron/blob/main/images/Screen%20Shot%202021-11-12%20at%207.18.50%20PM.png)

During the test , a blind  person was  asked to walk through an area  where we placed different types of obstacles within 20 meter range. The blind person walking speed was recorded. Time taken by the blind person before training and after training was successfully recorded as shown  in Fig.  17. Then  we calculated  the average  speed of the blind person after training to be 0.792 m/s which is similar to the speed that was achieved in [2] by using Blind walking stick and before training  to be 0.312 m/s. In comparison  with the traveling speed of the normal people which is 1.4 m/s on average, this result shows that training of the blind person actually increased the  traveling speed by more than 2 times.
It is also noted that the speed with which the system is responding after detecting an obstacle started decreasing as the walking speed of the blind person started increasing and walking with a speed more than 3km/hour(0.833 m/s) led to collision with the obstacles.

![alt image](https://github.com/saisravan549/Blinds_Apron/blob/main/images/Screen%20Shot%202021-11-12%20at%207.19.02%20PM.png)

We have also examined the responsiveness of our vibrating motors which serves the important purpose by indicating the threat around the blind person. It turns out that as shown in fig 19, there is a time gap T3 between the initial point when the VL53L1X sensor actually logs the distance of the obstacle which is below 30cm by default into the system and the point at which the vibrating motors actually start vibrating. This latency turns out to be really small with average being 710 milliseconds.And also it should be noted that the vibrating motors wont stop as soon as obstacle is disappeared from the sight of the sensor, but would take some time which is interestingly almost equal to the latency T3. FIG. 20 depicts graphically the latency measured for a total of 7 obstacles encountered by the user. 

![alt image](https://github.com/saisravan549/Blinds_Apron/blob/main/images/Screen%20Shot%202021-11-12%20at%207.19.26%20PM.png)


Several factors should be considered as discussed in [2] to evaluate the efficiency and performance of the proposed system such as the response time, range of detection  and power consumption.
The  first factor is the response time of the system, and a system detecting and responding within 0–100 milliseconds  is  considered as fast, 100–200 milliseconds as medium and higher than 200 milliseconds as slow system. The proposed system,Blind’s Apron, falls under fast systems and it has to be fast since our main aim for designing this system to make the response of the system as fast and as accurate as possible.
The second factor  is the range of detection. Generally, a device which can detect obstacles within 0-2 meters can be considered  as  a  low range  device,  2-4 meters can be considered as  medium range devices,  while  higher  than  4m  is  considered  as a high range device. The proposed system has a range of detection up to 4 meters operating at different modes using VL53L1X.
The third important factor is the power consumption of the system  and the amount of time it will work without the need to recharge. Generally,  consumption  of an  electrical power of  0.5W is considered as a low power consumption system, 0.5–1W as medium power  consumption system,  and  higher  than  1W  is considered as a high power consumption system. The current proposed system comes under a high power consumption system. Since the system is designed at a human body level and with additional activities like cloud interactions , it is not surprising to notice that the power consumption of the proposed system to be in high power consuming systems. But the operating voltage and current in the proposed design won't cause much harm to the user and also the design is made with  much care such that none of the electrical equipment will be in direct contact with the user.

![alt image](https://github.com/saisravan549/Blinds_Apron/blob/main/images/Screen%20Shot%202021-11-12%20at%207.19.36%20PM.png)

