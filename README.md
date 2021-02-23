
# Homebridge August Smart Locks Plugin

This project is a homebridge plugin for August smart locks.
A internet connected August Smart Lock is required for this plugin to work.
It can be connected via the August Connect Bridge Accesory

The August smart locks are exposed as a lock in HomeKit with support for:
- Lock/Unlock

DoorSense™ is exposed as a Contact Sensor in HomeKit with support for:
- Open/Closed
- Automation based on sensor status is now available
- August Wi-Fi Smart Lock Gen4: Door sensor is not available in HomeKit using the official HomeKit installation.

## Installation

Please install the plugin with the following command:

```
npm install -g homebridge-august-smart-locks
```

or use the Homebridge Web Interface to setup the Plugin by searching for 'august'

## Configuration

```json
{
    "platforms": [
        {
            "platform": "AugustLocks",
            "email": "<YOUR-EMAIL-ADDRESS>",
            "phone": "<YOUR-PHONE-NUMBER>",
            "password": "<YOUR-PASSWORD>",
            "code": "<2FA-CODE>",
            "installId": "<RANDOM-STATIC-STRING>",
            "hideLocks": "<lockId>,<lockId>"
        }
    ]
}
```

### Required Fields:

**email**: The email address of your August account.

**phone**: The phone number associated with your August account (e.g +123456789). Specify phone or email, not both. 

**password**: The password of your August account.

**code**: The 6 digit 2 factor authentication code August emails you when the plugin authenticates with August's API. When first setting up this you should configure all other required fields, restart homebridge, wait for the email from August, enter the 6 digit code into this configuration and then restart homebridge one last time. Subsequent restarts should remember your authenticated, however you may still receive an email when the homebridge restarts or the plugin encounters an error, you can safely ignore the subsequent emails from August.

**installId**: A random string used to identify this homebridge instance as an authorized application to your August Account. It need to be random and unique and you should never change it or you will have to reauthenticate with the 2FA Code.

### Optional Fields:

**hideLocks**: Commas Separeted String of all the Lock ID's you dont want to show in homekit. These are shown in the log of homebridge after the home and name of the lock is printed out on the prior long entry. you can use this to hide august locks in your august account you dont want to be part of the homebridge setup for example I use this on my August locks that are homekit capable.

**securityToken**: Augusts API Key, currently pulled from a decompiled apk of the August Android App, August may change this api key as they so wish to. Ese this property to update it if you follow a procedure to obtain the current api key for Augusts API Server.

**longPoll**: duration in seconds that the plugin will poll the api for status changes to keep the lock current when there isnt any major state changes

**shortPoll**: duration in seconds that the plugin will poll the api for status changes to keep the lock current when there is any major state changes


## Usage

* When you change the HomeKit switch to locked, the smart lock with lock the door.
* When you change the HomeKit switch from locked to unlocked the smart lock will unlock the app.
* When you use siri to unlock the door, it will unlcok the door and inform you of the status.
* When you use siri to lock the door, it will lock the door and inform you of the status.

## Tested

* Tested and Developed for August Smart Lock Generation 3 (non pro) because it has a more intuitive interface for the deadbolt and it way cheaper than the pro.
* Tested with August Smart Lock Pro 2nd Generation non WIFI model.
* Tested with August Wi-Fi Smart Lock (Gen4).

## Thanks

Thanks to all current and future pull request contributors. Feel free to add your contributions to this list in your pull request if you would like to.

Special thanks to @ryanblock from [Repo](https://github.com/ryanblock/august-connect) for providing a simple way to communicate with the August API in NodeJS.

Special thanks to @dejaloomer from [fork](https://github.com/dejaloomer/homebridge-augustlock) for providing the most recent fork update.

Special thanks to @llluis from [fork](https://github.com/llluis/homebridge-augustlock) for providing a reworked fork of the original forks.

Special thanks to @msutara from [fork](https://github.com/msutara/homebridge-augustlock2) for providing the ground work from 2 years ago.

Special thanks to @julianfez from [fork](https://github.com/julianfez/homebridge-augustlock2) for providing the original plugin from 4 years ago.
