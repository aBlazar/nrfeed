# nrfeed
podcast feeds for NPR shows

A simple flask app that uses the NPR API to generate rss feeds for All Things
Considered, Morning Edition, Weekend Edition Saturady and Weekend Edition
Sunday.

## Purpose

The podcast feeds that NPR provides for their news programs (All Things
Considered, Morning Edition, Weekend Edition) only contain 15 results.
Typically more than 15 audio segments are published per day. Additionally, the
same generic podcast image is used for each of these feeds, making it hard to
identify the podcast in a podcast app.

## How It Works

We use the public NPR API to request a "Podcast" feed for each program. The API
allows us to specify how many episodes to return, currently this is set to 50
which should provide 2-3 days worth of material for All Things Considered and
Morning Edition.

The following modification are made to feed returned by the API

   - Podcast title: remove phrase "NPR Programs: " from title
   - Podcast image: replace generic npr image with show specific image


## Testing

 - install python-flask and python-flask-cache `$ yum install python-flask python-flask-cache`
 - run `$ python wsgi.py`
 - open 'http://localhost:5000'

## Screenshots

### Firefox
![Firefox](/img/firefox.png?raw=true)

### Pocket Cast (Android)
![Pocket Cast](/img/pocketcast.png?raw=true)

## Requirements
  - python-flask
  - python-flask-cache

## Installation
This is a flask application. There are numerous installation guides online.
Each environment is different.

  - install as a flask app using your webserver of choice
  - copy settings.py.dist to settings.py
    - update `SERVER_NAME` and `API_KEY` variables
    - API_KEY can be obtained from your NPR profile page
  - copy `nrfeed.service` to `/etc/systemd/system/nrfeed.service`
  - modify paths in 'nrfeed.service` as necessary

