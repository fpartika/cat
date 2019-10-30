# cat
Protect your garden against cats
--------------------------------

If you already had cats visiting your garden then you understand my motivation for this project. What about using computer vision to help? 

Story
Almost one year ago we moved from an apartment to a house together with our cat and baby daughter, we wanted more space and why not having a garden. The nightmare has started when our cat started using the garden as a toilet. 
There was several tries to push him to come back to the cat litter, but all of them didn’t succeed, he really liked the  garden as much as we do. So I started thinking about something which could prevent the cat to go there, initially I thought about ultrasonic speaker or compressed air to scare him. But both are not good for open spaces. 
Then I thought about an presence sensor spraying water, but I did not want my baby daughter to get wet instead of the cat, so this problem  required a more sophisticated approach. A computer vision system which could differentiate between a person and a cat, interpreting images from a live camera and triggering a Solenoid valve which can sprinkle water in the naughty cat. 

To have more fun
Ive added a video recording feature, in order to monitor the cat behavior.

Camera position and light conditions
The initial position was too overshadowed generating false recognitions, and also the camera was too high in the wall making the detection more difficult.  

Cat learning curve
The cat tried several different strategies before giving up, first he found a blind spot which forced me to reposition the camera,  then he noticed that during the night it was harder to be detected, so I had to install a garage light activated by motion. Don't underestimate cats! 

Software
The Raspberry preparation is the most difficult part, the best guide I've seen is comming from www.pyimagesearch.com/2017/09/18/real-time-object-detection-with-deep-learning-and-opencv/
Which also provided a very comprehensive object detection concept explanation,  by the way this was what I used as a base for my project. Many thanks to Dr. Rosebrock!!.
The algorithm is a quite simple,  everything is build around the inference loop, which takes a image from video stream and passes it thru the deep neutral network in openCV.
Luckily this task doesn't require too much computer power considering an light network architecture as Mobilenet,   so a Raspberry is enough for the required FPS, there are several pre trained models available in the internet. 
I utilized a SSD Mobilenet trained in Pascal VOC dataset , which recognizes 20 classes including persons and cats what is perfect. Anyhow you can use another trained network without significative changes in the code.
Additionally there is a check in the main loop for checking if the button is pressed, due to the interference times, it requires to keep the button pressed some seconds. This is a bonus feature when you want to water the garden.
My system performs about .5 FPS what is enough for the task but not a good rate if you need to monitor quick changes, but again this was enough for the purpose of the project. 

Additional enhancements are possible to enhance performance, such as:
Split interference in a different threat 
Utilize a faster SD card
Raspberry 4
Use another network architecture as faster R-CNN, Yolo
