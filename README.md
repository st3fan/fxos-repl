
Quick docs for the 9.30pm release. More to follow tomorrow.

This thing works but it is far from complete. If you have feature requests then please submit pull requests or file a bug.

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

