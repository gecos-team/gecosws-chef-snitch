GECOS Chef Snitch
=================

**GECOS Chef Snitch** is an utility that can be used from a chef-client wrapper to notify about certain events. These events can be consumed (through DBus) from any 3rd party application such as a desktop applet so they can provide real-time information to the user.

In order to provide such feature, **GECOS Chef Snitch** comes with the following two components:

 - **gecosws-chef-snitch-service**: The DBus service
 - **gecosws-chef-snitch-client**: The commandline utility

gecosws-chef-snitch-service
---------------------------

**gecosws-chef-snitch-service** is a DBus system service that should be run as root, and it includes the following methods and signals.

__Methods__

 - GetActive
 - GetMessage
 - SetActive
 - NotifyMessage

__Signals__

 - IsActiveHasChanged
 - MessageNotified

gecosws-chef-snitch-client
--------------------------

**gecosws-chef-snitch-client** is a commandline utility that should be used from a chef-client wrapper to notify about certain events:

 - chef-client is working
 - chef-client has finished
 - notify a message so it can be shown to the user through a desktop applet

__How to use it__

<pre>
usage: gecosws-chef-snitch-client [-h] [--get-active] [--get-message] [--set-active {true,false}] [--set-message MESSAGE]

GECOS Chef Snitch client.

optional arguments:
  -h, --help            show this help message and exit
  --get-active          returns current status, either true or false
  --get-message         returns latest message delivered
  --set-active {true,false}
                        set the current value of active
  --set-message MESSAGE
                        provide a new message (use double quotes)
</pre>

__Examples of use__

<pre>gecosws-chef-snitch-client --get-active // show if active is 'true' or 'false'
gecosws-chef-snitch-client --set-active true // set active to 'true'
gecosws-chef-snitch-client --get-message // show the latest notified message
gecosws-chef-snitch-client --set-message "Deliver this message" // deliver the double-quoted message to the service
</pre>

