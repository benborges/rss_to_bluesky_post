## Use this code in a basic shell context
Script to automatically post RSS to Bluesky
overview

### steps to prep

$ pip install --upgrade pip
 
$ pip --version

$ pip install virtualenv

$ virtualenv -p python3 bluesky (name of your env)

$ source bluesky/bin/activate

$ pip install -r requirements.txt

### modify bluesky_post.py

    ATP_HOST -- Fill in your Bluesky host name Example: https://bsky.social
    ATP_USERNAME -- Enter your username Example: benbo.bsky.social
    ATP_PASSWORD -- enter password
    RSS_FEED_URL -- Enter the URL of the RSS feed you want to get data from. Example: RSS feed URL

## old instruction for Eventbridge context
Basically, referring to this Python script, I just read RSS and made it work with lambda.

TwitterToBluesky-bluemo-public

https://scrapbox.io/blu3mo-public/TwitterToBluesky
How to make it a zip file

We will hit the command as follows in the local environment where Python3.10 is installed. (mac only)

$ python -m venv venv

$ source venv/bin/activate

$ pip install -r requirements.txt

Go to the venv/lib/python<Python version>/site-packages directory and copy all dependencies to the same directory as your Lambda function code.

Finally compress the directory into a ZIP file.

cd lambda_package
zip -r ../lambda_package.zip .

Create a lambda function and set environment variables.

The environment variables are below.

    ATP_HOST -- Fill in your Bluesky host name Example: https://bsky.social
    ATP_USERNAME -- Enter your username Example: yuki2021.bsky.social
    ATP_PASSWORD -- enter password
    RSS_FEED_URL -- Enter the URL of the RSS feed you want to get data from. Example: https://www.ituki-yu2.net/rss

After that, if you run it with EventBridge, it will post the latest blog article to Bluesky at the specified time.
important point

    Handlers for runtime settings bluesky_post.lambda_handler.
    Timeout is about 1 minute.
