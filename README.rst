Mac OS Sandbox Profiles
=======================

To prevent application security issues to compromise your system, it is possible
to run them inside a ``sandbox`` in OSX. I started writing some sandbox files.

E.g. http://www.purehacking.com/blogs/gordon-maddern/skype-0day-vulnerabilitiy-discovered-by-pure-hacking

Problem
-------

To let any application run inside the sandbox, there has to 
- exist a sandbox file, that grants enough permissions
- be modified to original application package, to "bridge" the applications binary
  to a sandboxed version. 

The first point is pretty easy to build, the second point is a bit insecure as an
application could overwrite our "bridged starter" via update. If there is a good 
idea in someones' mind, let me know. 

Howto Do
--------

Checkout the repo to ``/Users/Shared/macos-sandbox-profiles``

Do the following actions to protect Skype and Firefox (which is currently provided
here). Further applications will be supported the same way. 

::

    cd /Applications/Firefox.app/Contents/MacOS/
    sudo mv firefox-bin firefox-bin.real
    sudo ln -sf /Users/Shared/macos-sandbox-profiles/bin/firefox-bin .
    
    cd /Applications/Skype.app/Contents/MacOS/
    sudo mv Skype Skype.real
    sudo ln -sf /Users/Shared/macos-sandbox-profiles/bin/Skype .
   
Issues
------

- Currently its not possible to allow firefox to start e.g. ``Preview.app`` to display
  pdf files out of the browser. There has to be made a download in before, which is 
  not as convenient as it could be. Please tell me how to do it, if you know.
