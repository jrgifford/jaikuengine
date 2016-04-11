# Introduction #

Getting a Jaikuengine instance running on Google App Engine is probably a lot easier than you think. Still, it's not for everyone, at least not without instructions. So here goes.

# Preconditions #

  * OS X
  * Python 2.5 or 2.6 (I assume 2.4 and 2.7 works too)
  * PIL (python-imaging), docutils and mox

# Installing #
Using macports, it should be as simple as the following:

  * Install [Macports](http://www.macports.org/install.php) according to the instructions.
  * `sudo port install subversion`
  * `sudo port install py25-pil` or `sudo port install py26-pil` (Python 2.5 and 2.6 respectively)
  * `sudo port install py25-docutils` or `sudo port install py26-docutils`
  * `sudo port install mox`

Observe that you can't (easily) run Jaikuengine in a virtualenv so `sudo` is the way to go for the moment.

## Checking out Jaikuengine ##

  * `svn checkout http://jaikuengine.googlecode.com/svn/trunk/ jaikuengine`
  * `cd jaikuengine`

## Local settings ##
Take a look at both `settings.py` and `local_settings.py` if you're interested in seeing how Jaikuengine can be configured. You can use `local_settings.py` to override settings in `settings.py`.

  * `cp local\_settings.example.py local\_settings.py

## Run locally ##
The below loads test data, changes you make will be overwritten next time you run it. The advantage is that you have a few users and channels already defined.

  * `python manage.py testserver common/fixtures/*.json`

Browse to http://localhost:8080 and log in as username and password "popular".

If you want to run without test data, use the following:

  * `python manage.py runserver localhost:8080`

Browse to http://localhost:8080/install to install the root user. Afterwards, click sign up to create your user.

If you want to start over with a fresh local database, run the following:

  * `python manage.py flush`

## App Engine setup ##

Login to https://appengine.google.com/ and create an application.

Now we need to configure some things. Let's assume you named your application "helloworld":

  * Fill in your application name on the first line of `app.yaml` as below:
```
  application: "helloworld"
```
  * `python manage.py config --write-to-file`
```
  Enter a site name []: Hello World!
  Enter a secret key [a259515a9b1369b9349b12ce15c2a943]:
  Enter an appspot domain []: helloworld.appspot.com
  Enabled Hosted Domains (yes|no) [yes]: no
  Enter your namespace domain [helloworld.appspot.com]:
  Enter the nick for your admin user [admin@helloworld.appspot.com]:
  Enable SSL login (yes|no) [yes]:
  Enter an email address to send from []: your-email-address@gmail.com
```

Now do a quick verification of `local_settings.py` to see that it looks like you expected.

## Deploying to App Engine ##
  * `python manage.py update`

While running the update script, you'll have to enter the email address and password you use to log into Google App Engine.

When the update script has finished, browse to http://helloworld.appspot.com/install (remember to replace helloworld with your App Engine application name) and create a root user.

Now sign up and start using your own instance of Jaikuengine! :)

## Email queues, etc. ##
In order to process some of queues, you might have to kick jaikuengine by browsing to http://helloworld.appspot.com/_ah/queue/default?secret=SECRET (replace "helloworld" by your application name and "SECRET" with what is defined by `settings.py` and `QUEUE_VENDOR_SECRET`)

## Running the test suite ##
After checking out jaikuengine and copying `local_settings.example.py` to `local_settings.py`, it's a good idea to run the test suite. You run it as follows:

  * `python manage.py test`

It will print out a lot of things, including warnings, before hopefully ending with "OK". If not, check the errors and post a question on channel #jaikuengine on http://jaiku.com.