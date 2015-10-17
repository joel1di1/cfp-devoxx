# How-to reset your CFP and prepare the Database for a new year

This document describes how to upgrade and to prepare your CFP for a new edition. 

# Do a backup of the HTML program

First, if you used the Publisher component, you should do a backup of all your program pages. To do so, we recommend that you use [wget](http://linuxreviews.org/quicktips/wget/) with a recursive option. 
 
To save the Devoxx France 2015 content : 

    wget -r http://cfp.devoxx.fr/2015/index.html
    ...
    ...
    
    cfp.devoxx.fr/2015/talk/FAA-6366/Participez_ 100%[================================================================================================>]   5.79K  --.-KB/s   in 0.003s 
    
    2015-10-17 10:41:53 (2.18 MB/s) - 'cfp.devoxx.fr/2015/talk/FAA-6366/Participez_a_JHipster' saved [5930/5930]
    
    --2015-10-17 10:41:53--  http://cfp.devoxx.fr/2015/speaker/blog.boulay.eu
    Reusing existing connection to cfp.devoxx.fr:80.
    HTTP request sent, awaiting response... 404 Not Found
    2015-10-17 10:41:53 ERROR 404: Not Found.
    
    FINISHED --2015-10-17 10:41:53--
    Total wall clock time: 42s
    Downloaded: 501 files, 5.0M in 3.8s (1.31 MB/s)
    
You can then upload the set of HTML files to a Wordpress/static web server. The Publisher URLs are defined with .html so that the content is easy to scrap.
    
# Keep a backup version of your Redis database

Before any operation from the Admin panel, make a copy of your redis dump file and the AOF file. Just in case...

# Create a tag on Github

On the dev branch, create a tag such as `DevoxxFR_2015_Backup`, in order to be able to compare between years.

# Start with the configuration 

Update `ConferenceDescriptor.scala` and start to edit the year. 

# Edit the messages

Edit and replace the year in the conf/messages.properties text file.

# Archive talks and reviews

As a super-admin, go to `/cfpadmin/attic/home` 
The Attic is a specific part of the CFP that has been designed to archive all talks and reviews. This is not part of the admin navigation bar on purpose. Only a super-admin with a deep knowledge of the CFP should use this section.

As explained, you should have a backup of your Redis database somewhere, before you start to trigger the clean-up.
Click on each button, and wait for the completion.
Once completed, the program is unpublished, each speaker sees the list of talks as "archived".
You can also reset the list of invited speakers.

# Remove agenda

Go to the [Angular Schedule application](/assets/angular/index.html) and delete all the schedules.

# Reset wishlist

Go to the Wishlist panel and delete all wishlist items.

You're good to go!

# Side note 

Any contribution and better documentation on this process is welcome.
Please update or correct this document with a Pull-Request. 
    