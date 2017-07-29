---
title: Google Chrome Remote
permalink: "/Google_Chrome_Remote/"
layout: default
category: software
---

Attaching to the Existing X Session in Ubuntu
---------------------------------------------

    https://chrome.google.com/webstore/detail/chrome-remote-desktop/gbchcmhmhahfdphkhkmpfmihenigjmpp?hl=en

    This is the bad old version: https://productforums.google.com/forum/#!topic/chrome/LJgIh-IJ9Lk

    And this is the version that works:
    https://plus.google.com/+FrancoisBeaufort/posts/2fHNvGUHJ3B


    stop it:
     /opt/google/chrome-remote-desktop/chrome-remote-desktop --stop

    Back it up:
    cp /opt/google/chrome-remote-desktop/chrome-remote-desktop /opt/google/chrome-remote-desktop/chrome-remote-desktop.orig

    Edit:  /opt/google/chrome-remote-desktop/chrome-remote-desktop

    OPTIONAL: Change this to the size I wanted.
    DEFAULT_SIZES = "1920x1080"

    REQUIRED: Change this to desktop zero which is the console.
    FIRST_X_DISPLAY_NUMBER = 0

    REQUIRED: Comment this out so it doesn't increment for a new desktop.:
    #while os.path.exists(X_LOCK_FILE_TEMPLATE % display):
    #  display += 1

    REQUIRED: Make the following section look like this:
      def launch_session(self, x_args):
        self._init_child_env()
        self._setup_pulseaudio()
        self._setup_gnubby()
      #  self.launch_x_server(x_args)
      #  self.launch_x_session()
        display = self.get_unused_display_number()
        self.child_env["DISPLAY"] = ":%d" % display

    Start it:
     /opt/google/chrome-remote-desktop/chrome-remote-desktop --start

    DONE. Now it attaches to the existing X Server on display :0. without springing errors and starting a new desktop ontop of your existing console (i.e.e the errors).﻿
