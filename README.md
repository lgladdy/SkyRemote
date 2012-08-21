SkyRemote
=========

A python based remote control for Sky+HD boxes updated to Picasso.

Based on Craig Heffner's Miranda, which is currently on Google Code http://code.google.com/p/miranda-upnp/ and licensed under GPLv3.


How does it work?
------------------------------------------------

Since Sky's Picasso update for Sky+HD boxes earlier this year, the Sky+HD box (DRX890 and DRX895, at present) boxes expose a DNLA server which, until the recent iPad application, was for an unknown reason.

This DNLA server exposes 5 control endpoints that can be used to control the Sky+ box over IP.

Miranda is a UPnP browser that lets you browse a UPnP client, and while the Sky+HD box requires a few specific changes to work with it, it pretty much does the job of browsing available methods, and lets you send things to it.

SkyRemote makes this a bit easier, by completely automating the detection of a Sky+HD box and loading the relative xml files to provide the data, and giving a simple "control" command which allows you to perform any of the "SkyPlay" control endpoint methods. These are currently:

* `GetMediaInfo_Ext`
* `X_NDS_SetUserPIN` Send the user's PIN (Used to unlock pre-watershed channels and recorded programming)
* `Play` Equivalent of "Play" button (prompts for play speed, can be used to fast forward)
* `Pause` Equivalent of "Pause" button
* `GetPositionInfo`
* `GetMediaInfo`
* `GetTransportInfo`
* `Stop` Equivalent of "Stop" button
* `GetDeviceCapabilities`
* `Next`
* `X_NDS_GetCACondition`
* `SetAVTransportURI`
* `GetTransportSettings`
* `Seek`
* `GetCurrentTransportActions`
* `Previous`

Please excuse any undocumented functions, I'm still figuring all this out.
You'll be prompted for any required arguments.

You can view the full, complete list of endpoints which are exposed by this using the command:
    
    host details 0

You can then send a raw command with:
    
    host send 0 SkyControl [SkyPlay|SkyRC2|SkyCM2] <command>

More information on the Sky DNLA Remote service is on my blog, at [www.gladdy.co.uk/blog](http://www.gladdy.co.uk/blog)