Your Own ZNC Bot On dotCloud
============================

ZNC is an IRC bouncer. Instead of connecting directly to an IRC
network, you connect to ZNC, and ZNC connects to the IRC server.
When you disconnect, ZNC keeps running, and remains in the channels
you joined. It will log messages while you are away, and replay
them when you reconnect. Also, when you are disconnected, it
automatically changes your nick by prefixing it with ``zz_``.

To run your own ZNC bouncer on dotCloud, just do the following
(don't forget to change ``mylogin`` and ``somepassword``, of course)::

  git clone git://github.com/jpetazzo/znc-on-dotcloud.git
  cd znc-on-dotcloud
  dotcloud create bouncer
  dotcloud push
  dotcloud env set ZNC_USER=mylogin ZNC_PASS=somepassword
  dotcloud info znc

In the output of the last command, look for something like:

.. code-block:: yaml

   - name: irc
     url: tcp://bouncer-johndoe.dotcloud.com:12345

The last line contains the host (``bouncer-johndoe.dotcloud.com``)
and the port (``12345``) that you should enter in your IRC client.
Don't forget to specify the same login and password as you did on
the ``dotcloud var set`` line!


Custom Configuration
--------------------

The configuration is generated on-the-fly by the ``znc/run`` script.
So if you want to run a custom configuration, you should edit it
there, and push your service again.

.. warning::

   If you used ``git clone`` to initialize your local repository,
   remember that when pushing a git repository to dotCloud, you have
   to commit your changes, *or* push with the ``--all`` option!


Alternate Configuration Method
------------------------------

Note that instead of using ``dotcloud var``, you can also edit
``dotcloud.yml``, uncomment ``znc_user`` and ``znc_pass`` and set
them to whatever you like. Note that the run-time variables
(set with ``dotcloud var``) will override the build-time variables
(set in ``dotcloud.yml``).

See also the warning above about pushing a git repository.
