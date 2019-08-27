# AI-and-IoT-based-smart-forest-monitoring-and-food-quality-checking
AI and IoT based smart forest monitoring and food quality checking.
The whole project is a system for forest monitoring right from collecting essential data to checking the quality of forest produce:

1.ESP8266 based smart forest data monitoring(IOT):
      Sensor that provide essential data for monitoring of forest like temperature,humidity,soil moisture etc are attached to a tree.
      This box of sensors also has a HC05 bluetooth device.We then use smartphone app that is connected to this sensor box to give input         commands.
      In this app we can visualize the real-time data via cloud(Ubidot). In order to get extra data we can just use speech-to-text feature       that extracts other essential features like age of tree(from stress sensor) etc via Firebase.
      There are 3 sensors attached to esp module:
 * Soil moisture sensor (for moister detection)
 * Fire sensor(to detect forest fire)
 * Vibration sensor(to detect any illegal activities)

2.Deep learning for forest food quality testing.
AlexNet 
Arduino UNO or Raspberry pi 3 can be used.
      Here we make a conveyor system which can monitor the quality of forest produce.This system has a webcam connected to raspberry pi 3,       which is programmed using matlab.
      We consider this a classification problem , essentially involving training the cnn(Alexnet here) to differentiate between good and         rotten/bad produce.In order to make it more effecient we use transfer learning as the Alexnet is pretrained to recognise 1000             objects.
      Next we feed training images (here we have taken mango and orange fruit) each containing around 2000 image of good and bad produce.
      We then train the model and work on improving its accuracy.
      
AlexNet Architechture

<p align="center">
  <img src="https://www.learnopencv.com/wp-content/uploads/2018/05/AlexNet-1.png" width="800" title="hover text">
</p>

Input image for training should be of size 227 * 227


Dataset:
The dataset was created using google images.
total images for each classes:mango(850),orange(900)

accuracy(on test images): 0.896
