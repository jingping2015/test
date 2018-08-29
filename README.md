# Facebook Business SDK for Python

[![Build Status](https://travis-ci.org/facebook/facebook-python-business-sdk.svg)](https://travis-ci.org/facebook/facebook-python-business-sdk)

### Introduction

The Facebook <a href="https://developers.facebook.com/docs/business-sdk" target="_blank">Business SDK</a> is a one-stop shop to help our partners better serve their businesses. Partners are using multiple Facebook API's to server the needs of their clients. Adopting all these API's and keeping them up to date across the various platforms can be time consuming and ultimately prohibitive. For this reason Facebook has developed the Business SDK bundling many of its APIs into one SDK to ease implementation and upkeep. The Business SDK is an upgraded version of the Marketing API SDK that includes the Marketing API as well as many Facebook APIs from different platforms such as Pages, Business Manager, Instagram, etc.

## Quick Start

Business SDK <a href="https://developers.facebook.com/docs/business-sdk/getting-started" target="_blank">Getting Started Guide</a>

Python is currently the most popular language for our third party developers. `facebook_business` is a Python package that provides an interface between your Python application and <a href="https://developers.facebook.com/docs/business-sdk/reference" target="_blank">Facebook's APIs within the Business SDK</a>. This tutorial covers the basic knowledge needed to use the SDK and provide some exercises for the reader.

**NOTE**: ``facebook_business`` package is compatible with Python 2 and 3!

## Pre-requisites

### Register An App

To get started with the SDK, you must have an app
registered on <a href="https://developers.facebook.com/" target="_blank">developers.facebook.com</a>.

To manage the Marketing API, please visit your
<a href="https://developers.facebook.com/apps/<YOUR APP ID>/dashboard"> App Dashboard </a>
and add the <b>Marketing API</b> product to your app.

**IMPORTANT**: For security, it is recommended that you turn on 'App Secret
Proof for Server API calls' in your app's Settings->Advanced page.

### Obtain An Access Token

When someone connects with an app using Facebook Login and approves the request
for permissions, the app obtains an access token that provides temporary, secure
access to Facebook APIs.

An access token is an opaque string that identifies a User, app, or Page.

For example, to access the Marketing API, you need to generate a User access token
for your app and ask for the ``ads_management`` permission; to access Pages API,
you need to generate a Page access token for your app and ask for the ``manage_page`` permission.

Refer to our
<a href="https://developers.facebook.com/docs/facebook-login/access-tokens" target="_blank">
Access Token Guide</a> to learn more.

For now, we can use the
<a href="https://developers.facebook.com/tools/explorer" target="_blank">Graph Explorer</a>
to get an access token.

## Install package

The easiest way to install the SDK is via ``pip`` in your shell.

**NOTE**: For Python 3, use ``pip3`` and ``python3`` instead.

**NOTE**: Use ``sudo`` if any of these complain about permissions. (This might
happen if you are using a system installed Python.)

If you don't have pip:

```
easy_install pip
```

Now execute when you have pip:

```
pip install facebook_business
```

If you care for the latest version instead of a possibly outdated version in the
<a href="https://pypi.python.org" target="_blank">pypi.python.org</a> repository,
<a href="https://github.com/facebook/facebook-python-business-sdk">check out the
repository from GitHub or download a release tarball</a>. Once you've got the
package downloaded and unzipped, install it:

```
python setup.py install
```

Great, now you are ready to use the SDK!

## Bootstrapping

### Create test.py
Create a test.py file with the contents below (assuming your system is using python 2.7 and installed under /opt/homebrew. Update to your proper python location.):

```python
import sys
sys.path.append('/opt/homebrew/lib/python2.7/site-packages') # Replace this with the place you installed facebookads using pip
sys.path.append('/opt/homebrew/lib/python2.7/site-packages/facebook_business-3.0.0-py2.7.egg-info') # same as above

from facebook_business.api import FacebookAdsApi
from facebook_business.adobjects.adaccount import AdAccount

my_app_id = 'your-app-id'
my_app_secret = 'your-appsecret'
my_access_token = 'your-page-access-token'
FacebookAdsApi.init(my_app_id, my_app_secret, my_access_token)
my_account = AdAccount('act_<your-adaccount-id>')
campaigns = my_account.get_campaigns()
print(campaigns)
```
