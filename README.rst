Your Own ZNC Bot On dotCloud
============================


::

  git clone git://github.com/jpetazzo/znc-on-dotcloud.git
  dotcloud push bouncer znc-on-dotcloud
  dotcloud var set bouncer ZNC_USER=mylogin ZNC_PASS=somepassword
  dotcloud info bouncer.znc

