# Multiscreen Getting Started Guide


## Resources
- Multiscreen Development Guide - http://www.samsungdforum.com/TizenGuide/tizen1731/index.html
- Multiscreen SDK download page - http://www.samsungdforum.com/AddLibrary/MultiSdkDownload
- Multiscreen Cloud Launched App Examples - http://www.samsungdforum.com/TizenGuide/tizen1731/index.html#Sample-Applications
- More advanced cloud launched examples - https://github.com/MultiScreenSDK
- Multiscreen Installed App Examples - http://www.samsungdforum.com/TizenGuide/tizen4401/index.html

## How to get Multiscreen cloud launched app running on the TV?
1. Download sample cloud app - http://www.samsungdforum.com/TizenGuide/tizen1731/index.html#Sample-Applications
2. Build/run mobile app(s).
3. Host the 'dist' directory in the TV app somewhere where it can be accessed by the TV. (If you have node.js installed in the development machine, you can do `npm install`, followed by `gulp build` and `gulp server` to serve the TV app locally from your development machine).
4. Put the TV in development mode and register the IP of the device your mobile app is running on. (You need to do this so that mobile app can launch the TV app even before the app is submitted to Samsung and whitelisted).

## How to get Tizen installed app running on the TV?
1. Download sample Tizen installed app -  http://www.samsungdforum.com/TizenGuide/tizen4401/index.html
2. Build/run mobile app(s).
3. Build the TV app using the Tizen IDE (see below - How to get started with Tizen IDE)
4. Put  TV in development mode and register dev machine (see below).
5. Create a target on IDE that points to the  TV (Go to the Connection explorer panel -> Remote device manager icon and enter the the TV IP address (The TV and the dev machine has to be in the same network).
6. Run the project as a Tizen Web application (right click project -> Run as -> Tizen Web application).

## What 2015 TVs support Multiscreen?
- 2015 Smart TVs 5500 and above (except 6201, 6203).

## How to put the TV in development mode?
1. On TV, goto Apps =>My Apps and using the remote, enter 12345 in sequence.
2. Set Developer mode to On.
3. Input IP Address of client (on same WiFi).
4. Reboot TV.

## How to get started with Tizen IDE?
1. Download and install the IDE - http://www.samsungdforum.com/tizendevtools/sdkdownload
2. Run update Manager (Install all the "extras").
3. Launch IDE -> ~/tizen-sdk/ide/IDE.app
4. Import the downloaded sample project (as Tizen Web project).
5. Try building the project (will probably complain about cert).
6. Go to Preferences-> Tizen SDK ->Security profiles,
7. Create a new profile.
8. Generate a certificate.
9. Build the app again.
