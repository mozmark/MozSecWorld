MozSecWorld
=========
:D
Project [Website](https://wiki.mozilla.org/WebAppSec/MozSecureWorld).

Setup
========
 
* Get the repository: `git clone https://github.com/haoqili/MozSecWorld`

* Get the vendor: `cd MozSecWorld/vendor` and do `git clone --recursive git://github.com/mozilla/playdoh-lib.git .`

* Get Content security policy middleware:
 * `git clone https://github.com/mozilla/django-csp.git` and then `cd django-csp` and `python setup.py install`
 * If you don't have the setuptools module, do these things (e.g. Linux)
  * Download [the appropriate py version setuptools egg][3]
  * run `sudo sh setuptools-0.6c11-py2.6.egg` change for your version [doc][4]

* Get pip: `sudo apt-get install python-pip`

* Get bcrypt: `sudo pip install py-bcrypt`


# How I start
`workon playdoh` to go to Mozilla playdoh's environment

`mysql.server start` to start the MySQL database

`./manage.py runserver` starts the Django server so I can navigate to http://127.0.0.1:8000/msw/

# overview of files
    apps/msw/models.py --> mysql
    apps/msw/urls.py --> apps/msw/views.py --> apps/msw/templates/msw/*

# Addons
Add bleach: `pip install -e git://github.com/jsocol/bleach.git#egg=bleach` ... actually this has been updated to playdoh.
Download recaptcha-client http://pypi.python.org/pypi/recaptcha-client read http://curioushq.blogspot.com/2011/07/recaptcha-on-django.html

CEF: inside your project home dir, do: `pip install --no-install --build=vendor-local/packages --src=vendor-local/src -I cef` [for more info][1]

[Image Upload][2]
* PIL: inside your project home dir, do: `pip install --no-install --build=vendor-local/packages --src=vendor-local/src -I pil`
* Jpeg: `brew install jpeg`
* rebuild PIL: `pip install PIL==1.1.7 --upgrade`

# For HTTPS URL certificate checking
- Use PyOpenSSL and sockets, not urllib, because urllib's urlopen does not check the SSL server certificates [warning on urllib documentation](http://docs.python.org/library/urllib.html), thus becoming vulnerable to Man-In-The-Middle attacks.
--> PyOpenSSL install: `pip install pyopenssl`


License
-------
TBD

[1]: http://curioushq.blogspot.com/2011/07/django-playdoh-package-locations.html
[2]: http://curioushq.blogspot.com/2011/07/getting-image-upload-to-work-on-django.html
[3]: http://pypi.python.org/pypi/setuptools#files
[4]: http://pypi.python.org/pypi/setuptools
