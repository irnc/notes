* [error](error.png) seen after graphical login on Ubuntu 15.04
* 00:30 start solving issue
* error happens because of `xinput set-prop 12 274 -106 -106 # Reverse scroll, i.e. make it a natural scroll`
* until 15.04 this command allowed to have natural scrolling on touchpad
* removing this command prevents error
* logout, login
* scroll continue to behave as normal, e.g. natural
* go to System Settings ... > Mouse & Touchpad, check _Natural scrolling_ checkbox
* logout, login
* scrolling is un-natural
* thus there is a tweam somewhere deep, braking _Natural scrolling_ option as it is implemented in Mouse & Touchpad
