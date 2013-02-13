What is this?
=============

This is a very simple REPL for Firefox OS. It allows you to list the running applications and then connect a very simple JavaScript console to it. Expressions that you type in the console will be executed in the context of the application that you are connected to. Under the same security permissions.

*You will need a device running a debug version of Firefox OS with Marionette support included*

I put less than an hour into it so far. Will make much bigger improvements int he coming days.

If you have feature requests then please submit pull requests or file a bug.

How to get it going?
====================

One time setup of a virtualenv that contains the marionette client:

```
$ virtualenv env
$ source env/bin/activate
$ (cd B2G/gecko/testing/marionette/client && python setup.py develop)
```

Port forward Marionette on your phone to your workstation:

```
adb forward tcp:2828 tcp:2828
```

List the available applications (iframes):

```
$ source env/bin/activate
(env) $ ./fxos-repl.py list
app://costcontrol.gaiamobile.org/widget.html
app://homescreen.gaiamobile.org/index.html#root
app://gallery.gaiamobile.org/index.html
app://keyboard.gaiamobile.org/index.html
```

Connect to a specific app and execute commands:

```
$ source env/bin/activate
(env) $ ./fxos-repl.py connect app://gallery.gaiamobile.org/index.html
Connected to app://gallery.gaiamobile.org/index.html
>>> navigator.userAgent
Mozilla/5.0 (Mobile; rv:18.0) Gecko/18.0 Firefox/18.0
>>> document.URL
app://gallery.gaiamobile.org/index.html
>>> document.getElementById('pick-view').innerHTML

      <header id="pick-top">
        <button id="pick-back-button"><span class="icon icon-back"></span></button>
        <h1 id="pick-header" data-l10n-id="pickoneimage2">Select</h1>
      </header>

>>> 
```

