## Other Third-Party APIs

#### Objective

Students will understand how third-party libraries can aid them in performing tasks in an efficient manner, for web API requests and beyond.

Slides can be found [here](https://msgrasser.github.io/c4q-external-apis/).

#### Lesson (Morning)

##### Picasso

Picasso is a library for downloading, transforming, and displaying images from the web or a local resource.

> Demo

> Create an app that pulls an image from the web and displays it, then show how it can be improved with Picasso

##### ButterKnife

ButterKnife is a view injection library that dramatically simplifies the way UI elements are referenced and bound to from Activities and more.

> Demo

> Update the app to include ButterKnife to do some view binding, image resizing, as well as adding a button to play a sound when clicked

##### RetroFit + GSON

RetroFit is a library that takes the monotony and pain out of building and processing web requests. When coupled with GSON to parse JSON into native objects, they create a simple way to get information from the web into the form Android expects.

> Demo

> Create a skeleton for an app that lists GitHub repos for a given user

##### Parceler

Parceler allows the objects parsed by GSON to be easily passed in intents between classes in an efficient manner.

##### Dependency Injection and Dagger

Dagger is a Dependency Injection library that aids in the decoupling of complex data structures. We'll introduce the concept of Dependency Injection, and give a brief intro into Dagger and it's alternatives.

##### More Tools

We'll also cover a few other tools that can aid in general.

#### Bonus Do Now (Late Morning / Afternoon)

> Create an app using RetroFit that populates a listview with your repositories on github. You may find it helpful to use an online tutorial [such as this one](https://guides.codepath.com/android/Consuming-APIs-with-Retrofit) for reference.

## Exit Ticket  
Please submit the exit ticket [here](https://docs.google.com/forms/d/1R2EKzGCiIkN4qSuIYPC-gR0kf__lGs_1wtji9JtXNt8/viewform). 
#### Questions and Answers:
######Q1: What are 3 benefits of using ButterKnife for view binding?  
  
######A1: Any 3 of the following would suffice:  
Avoiding Common Pitfalls AUTOMATICALLY!  
Handling ImageView recycling and download cancelation in an adapter.  
Complex image transformations with minimal memory use.  
Automatic memory and disk caching.  
Image handling can often be accomplished in a single line  
Adapter Downloads (from web)  
Image Transformations (change your image in preset and custom manners)  
Local Resource Loading (drawables, local file location, File object)  
  
###### Q2: Why would you use RetroFit as opposed to the more traditional AsyncTask/HttpRequest?  

###### A2: This is a bit more open-ended than I'd like, but answers to the effect of one of the following should be accepted:  
Save time programming, spend your time working on something less trivial  
Less complexity for debugging  
Fewer lines of code  
  
###### Q3: What is the value of Dependency Injection?  

###### A3: We didn't explicitly cover this in the lesson, but I did leave it as an exercise to watch the video linked to in the slides.  In short, listing any of the following should be considered a correct answer:  
Reduced Dependencies  
Reduced Dependency Carrying  
More Reusable Code  
More Testable Code  
More Readable Code  
In addition to viewing the video, an elaboration on each of these can be found [here](http://tutorials.jenkov.com/dependency-injection/dependency-injection-benefits.html).  
