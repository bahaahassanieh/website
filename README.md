# foundation

This is the [Django][dj]/[Django CMS][djcms] project that runs <http://okfn.org>.

[dj]: https://www.djangoproject.com/
[djcms]: https://www.django-cms.org/

[![Build Status](https://travis-ci.org/okfn/website.svg?branch=master)](https://travis-ci.org/okfn/foundation)
[![Coverage Status](https://coveralls.io/repos/github/okfn/website/badge.svg?branch=master)](https://coveralls.io/github/okfn/website?branch=master)

## Prerequisites and assumptions

You must have the following installed:

- Python 2.7
- libmemcached (`brew install libmemcached` on Mac OS X using [Homebrew](http://brew.sh/))
- node

You may also wish to follow any install instructions inside a Python virtual environment. Explaining `virtualenv` is outside of the scope of this README, but [this tutorial might help](http://hackercodex.com/guide/python-development-environment-on-mac-osx/).

## Running in development

    pip install -r requirements.dev.txt
    pip install honcho
    npm install
    python manage.py migrate
    honcho -f Procfile.dev start

## Running on Heroku

Please note that the following are by no means full instructions. There are a
number of config variables that will also need setting before the application
will work. These will be documented in due course.

    heroku create
    heroku labs:enable user-env-compile
    heroku addons:add heroku-postgresql
    heroku addons:add mandrill
    heroku config DJANGO_DEBUG=false \
                  DJANGO_COMPRESS_OFFLINE=true \
                  ...
    git push heroku master
    heroku run python manage.py migrate
