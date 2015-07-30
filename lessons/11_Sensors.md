### Sensors
Led by Danny Chiao  
  
[Slides](https://docs.google.com/presentation/d/1iVoeseIk-VfCZSFPKWFwrbSKUo6Sjos4hzlkcDLfvOE/edit?usp=sharing)

#### Do Now  
Make an app that has two buttons: one that looks like a camera button and the other an audio recording button.

#### Morning Lesson
* Camera
* Location  

#### Morning Exercises  
Implement the camera button to take a picture. When the picture is taken, add it to a gallery of images on your app with the geolocated address of the current location printed out in an adjacent TextView.

#### Afternoon Lesson  
* Audio  
* Accelerometer  
* Touch  

#### Afternoon Exercises
Implement the audio recording button. When the audio is recorded, also add it to the gallery with the geolocated address printed in an adjacent TextView. This audio file should support play/pause when its added to the view.

Then, use the accelerometer so that tilting the device can scroll through the gallery.

#### Exit ticket
Please submit the exit ticket [here](https://docs.google.com/forms/d/1z3EZjY9QSVwUJbkTAXV5BfehhPl79SDBP7APvg7Yinw/viewform?usp=send_form).  
  
###### Exit Ticket Questions and Answers! :)  
1. How do you get the current user location just a single time? What are the main considerations to make when choosing how to get location updates?  
  Answer:   
  To query for the user's location a single time, construct a LocationRequest that specifies numUpdates of 1 (i.e. new LocationRequest().setNumUpdates(1)).  
  This location request can then be sent off to the system's FusedLocationApi with the API manager (i.e. requestLocationUpdates(GoogleApiClient client, LocationRequest request, LocationListener listener)). The location will later come back through the location listener on the same thread the request was fired on. Note that this is not a blocking call, so the location will not be immediately available to the app.  
  The main consideration is battery drain. One should aim to use as little battery as possible by setting an appropriate priority and interval on the LocationRequest. This ensures the location service will use as few sensors as possible (GPS, WiFi, Data, etc) to get the user's location as few times as possible.  
  Another consideration when constructing a LocationRequest is connectivity/location. If the user is indoors for example, GPS will not be very accurate.  
  
  
2. What do the different values in a SensorEvent mean?  
  The sensor values[] array is an integer array with three values. What the values mean differ by sensor, but in the context of accelerometers, they correspond to the phone's acceleration (in m/s^2) in different directions including an offset for the acceleration from gravity.  
values[0] is acceleration in the x direction.  
values[1] is acceleration in the y direction.  
values[2] is acceleration in the z direction.  
If a phone is resting on a table, the corresponding values would approximately 0, 0, and 9.8 (Earth's gravitational acceleration).    
