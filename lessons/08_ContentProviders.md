### Content Providers
Instructor: Yang Mou

#### Objective
Learn how to access and modify data from content providers.

#### Do Now  
Create an activity that lets users fill out an event title, description, and location. When users press the "Create event" button, it fires an intent and opens the calendar app with those fields pre-populated.

#### Lesson  

##### Content Providers and Content Resolvers
[ContentProviders](http://developer.android.com/reference/android/content/ContentProvider.html) present data that your app (or even other people's apps) can access. You can think of the data as being structured in tables, similar to SQL. You can also provide access to files that you own.

ContentProviders are particularly useful if:
* You want to offer complex data or files to other applications.
* You want to allow users to copy complex data from your app into other apps.
* You want to provide custom search suggestions using the search framework.

Android has a number of built-in ContentProviders, such as for interacting with the user dictionary, calendars, and contacts. 

[ContentResolvers](http://developer.android.com/reference/android/content/ContentResolver.html) are used to access and modify data presented in ContentProviders. We'll focus on working with ContentResolvers. In particular, we'll learn about how to work with calendars.

##### URIs and permissions
ContentProviders are accessed by using URIs. For example, to access calendars, we use URIs that start with `content://com.android.calendar`. 

ContentProviders often require the specific permsissions to use. For example, to read from calendars, we need `android.permission.READ_CALENDAR`. To modify them, we use `android.permission.WRITE_CALENDAR`.

##### Operations
ContentResolvers allow you the basic "CRUD" actions: create, retrieve, update, and delete. These verbs are recurring pattern when working with data and APIs.

##### Cursors
To read data, ContentResolvers use [Cursors](http://developer.android.com/reference/android/database/Cursor.html). Cursors are very similar to what you saw in SQL with minor differences. In order to use a Cursor, you have to specify:
* The table to read from
* Columns to include
* Criteria for selecting rows (optional)
* Sorting order (optional)

Once you have a cursor, you can go through the rows with a loop like `while (cursor.moveToNext()) { ... }`

##### Calendar Provider
The first table is Calendars, which contains all the calendars you have on your phone. Note one account can have multiple calendars, and you can have multiple accounts on your phone.

The second table is Events, which has rows for each calendar event. This contains information such as event title, description, and location.

Finally, there are three more tables that provide more information about each event: Attendees, Reminders, Instances (for recurring events.) We won't go into detail on these.

##### Unix Time
Side topic: Unix time is the amount of time that's passed since midnight UTC, January 1, 1970. This is how Unix-like systems and Android work with time. `System.currentTimeMillis()` will return the number of milliseconds since the start time. You can also get the value for a specific time by using the `Calendar` class.
```
Calendar today = Calendar.getInstance();
today.set(2015, Calendar.JULY, 21, 19, 0);
long millis = today.getTimeInMillis();
```

##### Additional Considerations
* Whereas all the examples were done on the main thread, this is ill-advised because it can lock up and crash your app. Use  [`CursorLoader`](http://developer.android.com/reference/android/content/CursorLoader.html) for a built in way to handle threading.
* Writing your own content provider is a bit complicated. Usually you won't have to do this unless you're exposing a complex amount of data to other apps.
* Sync adapters allow you to sync data between your app and a server. These often go hand in hand with content providers.

#### Exercises
* Modify your Do Now app to create a calendar event without firing an intent.
* Create an new app that lists all the calendars on your device. Find the ID of your favorite calendar.
* List all of your events from the month of July 2015.
* BONUS: When you click on an event, show a list of all the attendees of that event.

#### Resources
http://developer.android.com/guide/topics/providers/content-providers.html
http://developer.android.com/guide/topics/providers/calendar-provider.html
  
#### Exit Ticket
Please submit the exit ticket [here](https://docs.google.com/forms/d/1jj_DQk2J7Q0SfJPN7719AYa1DK4jPfDHdu5Ct4zDbyE/viewform).  
