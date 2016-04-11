# JaikuEngine #

JaikuEngine is a social microblogging platform that runs on [AppEngine](http://code.google.com/appengine).  JaikuEngine powers [Jaiku.com](http://www.jaiku.com).  For the mobile client source, see: [Jaiku Mobile client](http://code.google.com/p/jaikuengine-mobile-client/)

## Dependencies ##

  * Python 2.4 or 2.5
  * Docutils: http://docutils.sourceforge.net/
  * Mox: http://code.google.com/p/pymox/ version 0.5.1
  * Everything else should be included in the checkout via svn:externals.
  * If you're using Ubuntu you will need to install the pstats library which is in the python-profilers package.

## Quickstart ##

  1. Check out the repository (it's somewhat large due to image binaries): `svn checkout http://jaikuengine.googlecode.com/svn/trunk/ jaikuengine`
  1. Copy local\_settings.example.py to local\_settings.py
  1. Run the server with some test data pre-loaded: `python manage.py testserver common/fixtures/*.json`
  1. Browse to localhost:8080 and log in with popular/password

## Getting Running ##

Jaiku uses the Django framework as well as most of its development process,
so most actions go through manage.py.

To run the development server:

> `python manage.py runserver`

But most of the time you'll be wanting to load some basic test data, this can
be done with the testserver command (and specifying the data to load):

> `python manage.py testserver common/fixtures/*.json`

Both of these will start a server running at http://localhost:8000.


## Contributing to the project ##


We would be happy to consider any additions or bugfixes that you would like to
add to the helper. Please add them as a patch, in unified diff format to the [Issue Tracker](http://code.google.com/p/jaikuengine/issues/list).

Before we can accept your code you will need to have signed the Google
Contributor License. You can find this at:

http://code.google.com/legal/individual-cla-v1.0.html
or
http://code.google.com/legal/corporate-cla-v1.0.html

If you are an Individual contributor you will be able to electronically sign
and submit the form at the URL above. Please ensure that you use the same email
address to submit your patch as you used to sign the CLA.


## Reporting Bugs and Requesting Features ##

If you find a bug or would like to request a feature you may do so at the
Google Code issue tracker for this project:

http://code.google.com/p/jaikuengine/issues/entry