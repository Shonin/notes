date: 2016-02-29 01:56:36
name: google app engine for ubuntu
---
An (Ubuntu) Guide to Google App Engine
==============================
Specifically made for the "Developing Scalable Apps in Python" course on Udacity

There's a lot of info about doing this course on a linux machine, but I wanted to compile all the up to date info that I had about it in one place, for my reference and for yours. 

I'm running **`Ubuntu 15.10`**

Installing Google Apps Engine
=======================

**1)** Download the Google App Engine SDK for Linux / Python from this link: [Download here!](https://cloud.google.com/appengine/downloads#Google_App_Engine_SDK_for_Python)

**2)** You should check to make sure the download isn't corrupted or fraudulent. 

`sha1sum /path/to/google_appengine_1.9.33.zip`

This should give you an identical SHA1 Checksum as to the one you saw on the download page. As of Feb 28 2016, that value is `cd24fa67dc5ce32bb189579661bb899c13cf47f3`

**3)** I created a folder called 'lib' in my home directory, and I put Google App Engine in it. In this tutorial we'll be doing the same.

Navigate to your home directory and create a folder called lib
`cd`
`mkdir lib`

Move the app engine zip file there:
`mv /path/to/google_appengine_1.9.33.zip /lib`

Unzip the file:
`unzip lib/google_appengine_1.9.33.zip`

Delete the zip file
`rm lib/google_appengine_1.9.33.zip`

**4)** That's it, it's installed!

Setup Google App Engine 
===================
On Linux + Python, Google App Engine is used exclusively through the terminal by calling python files inside the Google App Engine folder we made inside lib.

**You do this by running something like:**
`python <app_engine_file> <your_app_folder>`

**For a more concrete example:**
`python lib/google_appengine/dev_appserver.py Dev/fsnd/conference/Lesson_2/000_Hello_Endpoints/`

*That's a lot of of paths to type!*

So instead of typing all that out every time let's setup an environment variable.

Open your `.bashrc` file and add this line to the bottom:

`export GAE=/home/<username>/lib/google_appengine`

Where `<username>` is your username (be sure to replace the <>)

Now instead of typing all those paths we can first navigate to the Lesson_2 folder:
`cd Dev/fsnd/conference/Lesson_2/`

**Then simply run**
`python $GAE/dev_appserver.py 000_Hello_Endpoints`

*Ahh, much better...*

Using Google App Engine
====================

You need to call different python files in the `$GAE` folder to perform different functions that you see Karl perform using the Google App Engine GUI on his Mac. 

**Running your App on Localhost**
`python $GAE/dev_appserver.py /path/to/your/app/folder/`

**Pushing your App into Production**
`python $GAE/appcfg.py update /path/to/your/app/folder/` 

**^^Make sure you get the `update` in that one^^**

API Explorer
==========
Due to a recent update in the App Engine you have to launch chrome with some special arguments when launching the API Explorer

Unless you installed chrome in anything but the default way, go into the terminal and run:

` /usr/bin/google-chrome-stable --user-data-dir=test --unsafely-treat-insecure-origin-as-secure=http://localhost:8080`

This will launch an instance of Chrome that you *should only use for the API Explorer*. It is safe to ignore the security warning that comes up when Chrome launches

Now you can navigate to [http://localhost:8080/_ah/api/explorer](http://localhost:8080/_ah/api/explorer)

**You can add the following line to your `.bashrc` file to make a shortcut for launching chrome for the API Explorer**
`alias apichrome="/usr/bin/google-chrome-stable --user-data-dir=test --unsafely-treat-insecure-origin-as-secure=http://localhost:8080"`

Then just type `apichrome` into the terminal to launch chrome for the API Explorer


Updates
=======
They will come as I proceed through the course.