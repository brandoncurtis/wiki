---
title: Python on the Web
permalink: "/Python_on_the_Web/"
---

Installing Apache and Flask
---------------------------

<https://www.digitalocean.com/community/tutorials/installing-mod_wsgi-on-ubuntu-12-04>

sudo apt-get install libapache2-mod-wsgi

Configuring Your Application
----------------------------

<http://www.subdimension.co.uk/2012/04/24/Deploying_Flask_to_Apache.html>

Next I created flaskTest.wsgi in my application's folder:

<code>

        import sys
        sys.path.append('/<redacted>/flaskTest')
        from flaskTest import app as application

</code>

I created a new Apache VirtualHost config in /etc/apache2/sites-available:

<code>

        <VirtualHost *:80>
            ServerName flasktest.subdimension.co.uk
            WSGIDaemonProcess flaskTest user=flask group=www-data threads=5 home=/<redacted>/flaskTest
            WSGIScriptAlias / /<redacted>/flaskTest/flaskTest.wsgi
            <Directory /<redacted>/flaskTest>
                WSGIProcessGroup flaskTest
                WSGIApplicationGroup %{GLOBAL}
                WSGIScriptReloading On
                Order deny,allow
                Allow from all
            </Directory>
        </VirtualHost>

</code>

Adding the WSGIScriptReloading directive meant that any time I made changes to my application files, I could simply $ touch flaskTest.wsgi and the app would restart with changes applied. I even found a python-based implementation of touch that I could use if I wanted to be able to restart the app from within the app!

As mentioned above, by default, the application starts as if it were called from the server root. The WSGI Documentation gave me the extra home option for the WSGIDaemonProcess directive, which changes that to wherever you want it.

Send Data from a Textbox
------------------------

<http://stackoverflow.com/questions/12277933/send-data-from-a-textbox-into-flask>

To Sort
-------

<http://flask.pocoo.org/> <http://flask.pocoo.org/docs/quickstart/> <http://stackoverflow.com/questions/5615228/call-a-python-function-within-a-html-file>

------------------------------------------------------------------------

### Installation

sudo apt-get install python-flask

------------------------------------------------------------------------

### Python Quickstart

<code>

    from flask import Flask
    app = Flask(__name__)

    @app.route("/")
    def hello():
        return "Hello World!"

    if __name__ == "__main__":
        app.run()

</code>

### Techniques

How to download a file generated on-the-fly in Flask <http://runnable.com/UiIdhKohv5JQAAB6/how-to-download-a-file-generated-on-the-fly-in-flask-for-python>

`   # We need to modify the response, so the first thing we `
`   # need to do is create a response out of the CSV string`
`   response = make_response(csv)`

`   # This is the key: Set the right header for the response`
`   # to be downloaded, instead of just printed on the browser`
`   response.headers["Content-Disposition"] = "attachment; filename=books.csv"`
`   return response`

------------------------------------------------------------------------

### Apache, WSGI, and Flask

<http://en.wikipedia.org/wiki/Web_Server_Gateway_Interface>

Here's a very straightforward tutorial:

<http://www.subdimension.co.uk/2012/04/24/Deploying_Flask_to_Apache.html>

and a more complicated official tutorial:

<http://flask.pocoo.org/docs/deploying/mod_wsgi/>

### Python Graphics Libraries

Python Library for Simple Drawing (pygame)

<http://stackoverflow.com/questions/326300/python-best-library-for-drawing>

Python Tutorial: Graphics

<http://anh.cs.luc.edu/python/hands-on/3.1/handsonHtml/graphics.html>

PyQGraph - Scientific Graphics and GUI Library for Python

<http://www.pyqtgraph.org/>

Python - Useful Modules

<https://wiki.python.org/moin/UsefulModules>

PyX - Python Graphics Package

<http://pyx.sourceforge.net/>

### Python Web Frameworks

Python - Flask Web Development Tutorial

<http://pythonprogramming.net/flask-web-development-tutorial/>

4 Python Web Frameworks Compared

<http://www.sixfeetup.com/blog/4-python-web-frameworks-compared>