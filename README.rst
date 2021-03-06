python-iploka-geoip
===================

The simplest possible way to get IP geolocation information in Python.

.. image:: https://raw.githubusercontent.com/whois-api-llc/python-iploka-geoip/master/images/geoip.png

.. image:: https://img.shields.io/pypi/v/iploka-geoip.svg
    :alt: python-iploka-geoip Release
    :target: https://pypi.python.org/pypi/iploka-geoip

.. image:: https://img.shields.io/travis/whois-api-llc/python-iploka-geoip.svg
    :alt: python-iploka-geoip Build
    :target: https://travis-ci.org/whois-api-llc/python-iploka-geoip


Meta
----

- Author: Randall Degges
- Email: r@rdegges.com
- Twitter: https://twitter.com/rdegges
- Site: http://www.rdegges.com
- Status: production ready


Prerequisites
-------------

To use this library, you'll need to create a free Iploka account:
https://api.iploka.com/

If you haven't done this yet, please do so now.


Installation
------------

To install ``iploka-geoip`` using `pypi <https://pypi.org/>`_, simply run:

.. code-block:: console

    $ pip install iploka-geoip

In the root of your project directory.


Usage
-----

Once you have `iploka-geoip` installed, you can use it to easily find the
physical location of a given IP address.

This library gives you access to all sorts of geographical location data that
you can use in your application in any number of ways.

.. code-block:: python

    from iploka_geoip import GeoIP

    geoip = GeoIP("your-api-key");

    try:
        data = geoip.lookup("8.8.8.8")
    except ConnectionError:
        # If you get here, it means you were unable to reach the geoipify
        # service, most likely because of a network error on your end.
    except ServiceError:
        # If you get here, it means geoipify is having issues, so the request
        # couldn't be completed :(
    except:
        # Something else happened (non-geoipify) related. Maybe you hit CTRL-C
        # while the program was running, the kernel is killing your process, or
        # something else all together.

    print(data)

Here's the sort of data you might get back when performing a geoip lookup
request:

.. code-block:: json

    {
      "ip": "8.8.8.8",
      "location": {
        "country": "US",
        "region": "California",
        "city": "Mountain View",
        "lat": 37.40599,
        "lng": -122.078514,
        "postalCode": "94043",
        "timezone": "-08:00"
      }
    }

By default, this library handles retrying failed HTTP requests for you. For
instance: if the Iploka API service is currently down or having issues,
your request will be retried up to three consecutive times before failing.


Changelog
---------

All library changes in descending order.

Version 0.1.0
*************

**August 4, 2020**

WhoisXML API Tech Support has fixed issues due to obsolete
commands. It is now Python 3.8 compatible, and has been also tested
with Python 3.6 and 2.7.


Version 0.1.0
*************

**Released April 26, 2018.**

- First release!
