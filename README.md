# FileShift

A node.js project to translate between various remote file system protocols.

A work-in-progress.  Currently provides some limited NetBIOS support.  The
current focus is on implementing SMB.  To follow along with the the latest
changes, see the [node-smb][] project.

Feedback, suggestions, and collaboration welcome!

## netbios-fwd

The `netbios-fwd` script will forward NetBIOS sessions from port 139 to the
direct SMB port, 445.  It will also advertise the machine it runs on using
NetBIOS broadcast messages.

To use, first modify the constants at the top of the `netbios-fwd` script:

``` javascript
var NAME = 'XYKON-2';
var SCOPE_ID = 'example.com';
var FWD_PORT = 445;
var FWD_HOST = '127.0.0.1';
```

Then run the script as root:

``` bash
sudo node netbios-fwd.js
```

Note, if you are on a Mac, you will need to disable the built in `netbiosd`
daemon:

``` bash
sudo launchctl unload /System/Library/LaunchDaemons/com.apple.netbiosd.plist
```

[node-smb]: http://www.github.com/wanderview/node-smb
