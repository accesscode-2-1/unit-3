## Broadcast Receivers
Instructor: Jared Poelman

#### Resources
http://developer.android.com/reference/android/content/BroadcastReceiver.html
http://developer.android.com/guide/components/processes-and-threads.html

#### Morning Lesson  
* Review of Intents 
* Sending a Broadcast  
* Receiving a Broadcast in an Activity  
* Receiving a Broadcast with the Manifest  

#### Morning Exercise  
Create an app to send and receive a simple Broadcast in the activity and the manifest.  

#### Pod Meetings  

#### Afternoon Lesson  
* Boot up and Battery changes  
* Security
* Ordered Broadcasts  
* LocalBroadcastManager  
* Receiver Lifecycle  
* Process Lifecycle  


#### Afternoon Exercise
Double up your BroadcastReceivers or create an app that starts on boot.

#### Exit Ticket  
Please submit the exit ticket [here](https://docs.google.com/forms/d/1YOnIqu8FAXkSjymIrOS3zUAvLyB0xrsZSKiKa2krMDk/viewform).  
  
Exit Ticket Questions & Answers:  

1) Two important parts of an intent:  
a) action to be performed  
b) data to be acted on  

1) What are the two ways you can register a Broadcast Receiver?	 
a) static (manifest)  
b) dynamic  

3) What is the process hierarchy?	  
How Android prioritizes processes (based on the stuff that's inside) - or, the actual hierarchy --  
foreground, visible, service, background, empty  

4) How do you control the order an ordered broadcast is sent?	  
Ordered broadcast with priorities  

5) What is an intent filter?  
List the actions of intents your broadcast receiver is interested in.  Declared dynamically or in the manifest.  
