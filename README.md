tweets
======

A WordPress short code plugin to display the tweets 

Create an app in twitter and get the oauth access token, oauth access token secret, consumer key and consumer secret.
This is the short code format.

            [mytweets atoken='XXXXXXXXXXXXXXXXXXXXXXXXXX' 
                      asecret='XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX' 
                      ckey='XXXXXXXXXXXXXXXXXXXX' 
                      csecret='XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX' 
                      handle='Twitter username']

Handle is the twitter username. Thats it the tweets will be displayed in a numbered format. For now I have 
hardcoded the number of tweets. Only the last 10 tweets will be returned. I have also added the functionality to remove '@RT' from the retweets. 
