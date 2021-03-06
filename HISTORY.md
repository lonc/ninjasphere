# 0.1.2 (2014-09-12)
" Wake me up before go wemo [:boom:](http://open.spotify.com/track/5J0S5UgpCwlmEagrqgzvoC) "

### Headline

It's been a massive few weeks. The hardware being done and dusted means we're all totally focused on completing the software. The big (but necessary change) to Go has gone very well, and we're seeing our productivity back to those heady node.js days.

This week *should* see the first release of the iOS mobile application, which we are extremely proud of (Android is next!)
Also, we'll be open-sourcing the first sections of Sphere! Starting with go-sphere (the base) and driver-go-hue. 

### Features

  * sphere-web-static: Added controls for the 'media-control', 'volume', 'color' and 'brightness' protocols
  * driver-go-wemo: Added. Exposes 'on-off' channel
  * driver-go-hue: Much improved. Updates state correctly
  * driver-go-lifx: Ported from Node.JS. Much lower memory usage than the node version
  * driver-go-sonos: Added. Exposes 'media-control' and 'volume' channels
  * sphere-go-homecloud: Added. Initially just updating Thing's locations as they arrive from the cloud. 
  * sphere-go-led-controller: Added. Controls on-off and light devices using a simple swiping pane interface
  * sphere-go-gestic: Ported from Node.JS

### Bug fixes

  * sphere-home-cloud: Fix re-syncing of deleted things/rooms
  * sphere: Massive drop in number of files and their size, which should mean for much faster updates
  
### Known Issues

  * sphere-web-static: Still no state reflected in the web ui.
  * location: Accuracy has been improved, but the "Production" cloud service has not been updated yet.
  * driver-go-lifx: Color can't be updated using the dashboard
  
  <img src="https://s3-ap-southeast-2.amazonaws.com/uploads-au.hipchat.com/25403/256486/jrgykF7PFwTdjLW/upload.png" />

# 0.0.8 (2014-08-07)

### Headline

The BLE driver used for positioning has been rewritten in Go(http://golang.org/) freeing up a LOT of ram and cpu time vs. the existing Node.JS version. We're currently doing the same for Lifx, ZigBee and the gesture interface.

### Bug fixes

  * driver-go-ble: Added, saves ~15mb ram. Just advertising for now, device drivers will be added next.

### Bug fixes

  * driver-intelligence: Fixed bug sometimes preventing the contextual lights from working early in the morning.

# 0.0.7 (2014-07-31)

### Headline
Ok, not a big release this week. A lot of heavy-lifting going on behind the scenes.

### Bug fixes
  * sphere-intelligence: Fix over-eager logging when grabbing weather, and an error message.

### Known Issues

# 0.0.6 (2014-07-25)
" I've been syncing about you [:satellite:](http://open.spotify.com/track/5ojjL1ypuOtqqOpb4QiM1M) "

### Headline
Data syncing between Home Cloud and the Ninja Cloud in preparation for thing intelligence. Rewrite of the Philips Hue driver in [Go](http://golang.org/) for improved performance and reduced memory footprint.

### Features
  * driver-hue: Rewritten in Go
  * sphere-home-cloud: Added support for data model syncing to/from ninja cloud
  * sphere-schemas: Extraction of timeseries properties from protocol events
  * sphere-home-cloud: Timeseries datapoints are now published to the cloud

### Bug fixes
  * sphere-common: Log errors in device batch set operations

### Known Issues

# 0.0.5 (2014-07-04)

" Bullet with notify wings (despite all my rage I am still just a configuration page) [:metal:](http://open.spotify.com/track/4qMzPtAZe0C9KWpWIzvZAP)"

### Headline
Various stability improvements and tweaks under the hood in preparation for notifications.

### Features
  * sphere-common: All service calls and return values are now validated at the target
  * sphere-common: Data in a device batch 'set' is now validated
  * sphere-schemas: Notification and configuration screen schemas
  * sphere-common: Driver configuration and notification events
  * driver-hue: Notifications in the driver
  * mqtt-bridgeify: Push more telemetry up to the cloud

### Bug fixes
  * sphere-director: Implemented a watchdog for internal services to improve stability
  * sphere-common: config - sphere_debug=true environment variable now works as expected
  * sphere-intelligence: Various tweaks and fixes in logic of ContextualLights
  * driver-lifx: Fix issue with renamed bulbs
  * various: Less chatty, more informative logging

### Known Issues
  * If no progress is received during calibration, the progress will dissappear after 45s

# 0.0.4 (2014-06-27)

" I can't stop loving hue [:sunglasses:](http://open.spotify.com/track/7apQOIhWnJnhGeuY9Muqu8) "

### Headline
Intelligence has began! Contextual lights managing Hue & LIFX.

### Features
  * sphere-intelligence: contextual lights!
  * sphere-web-static: On/Off buttons
  * sphere-web-static: UI for enabling contextual lights in a room.
  * driver-hue: enabled!
  * driver-lifx: enabled! (Note: LIFX firmware v1.2 required)
  * sphere-common: Add state batching and other protocol events
  * sphere-schemas: colour - Add temperature and x/y modes
  * sphere-schemas: Initial media and media-control protocols


### Bug fixes
  * sphere-common: Handle channels for non-existent protocols
  * sphere-zigbee: various fixes
  * sphere-web-static: Associated devices are now hidden from the find devices list
  * sphere-web-static: Clicking a room no longer restarts calibration

### Known Issues
  * The on/off buttons in the UI do not remember state

### Screenshots

<img src="https://s3.amazonaws.com/assets.sphere.ninja/img/sphere-dev-release-0.0.4-1" width="49%" />
<img src="https://s3.amazonaws.com/assets.sphere.ninja/img/sphere-dev-release-0.0.4-2" width="49%" />


# 0.0.3 (2014-06-20)

" I'm a socket man [:rocket:](http://open.spotify.com/track/2zvot9pY2FNl1E94kc4K8M) "

### Headline
Much more complete Sphere API, and some example applications using the ZigBee socket.

### Features
  * sphere-director: Enable driver-zigbee!
  * sphere-schemas: Services can now define required methods
  * sphere-common: Promises-based Sphere api e.g. ```Ninja.Sphere.rooms().then(function(rooms) {...})```
  * sphere-web: Can now update a thing name
  * sphere-web: Can now assign a thing into a room manually.
  * driver-zigbee: The power socket works (power and on-off protocols)

### Bug fixes
  * sphere-bluetooth-smart: Much lower CPU utilisation
  * Removed unused dependencies, fixed all JSHint warnings.

### Screenshots

<img src="http://i.imgur.com/WQuNMAH.png" width="49%" />
<img src="http://i.imgur.com/fYKSFBg.png" width="49%" />

---

# 0.0.2 (2014-06-13)

" apt, apt, baby [:icecream:](http://open.spotify.com/track/3U8271rQxTvf5SWXULGeO9) "

### Headline
Initial `thing` API

### Features
  * SphereAPI: Initial cut of Sphere API (Initially things only)
  * Reduce package size by 50% and huge speed increase when apt-get dist-upgrading
  * sphere-home-cloud: Far more responsive location events
  * sphere-home-cloud: Increased Model methods to make interaction more powerful
  * sphere-schemas: Schemas for location, illuminance, moisture
  * sphere-web: Expose module CPU & memory utilisation

### Bug fixes
  * Fix location channel not being created when adding a person
  * Fix 'not opened' error from WebsocketServer
  * Fix /etc/default/ninja overrides file not being present

### Screenshots

<img src="http://i.imgur.com/AxifF1Z.png" width="49%" />

---

# 0.0.1 (2014-06-06)

" If you're appy and you know it clap your hands [:clap: :clap:](http://open.spotify.com/track/5jigkWsgdwcjsdkZWN26zm) "

### Headline
Added JSON-Schema defined RPC-over-MQTT Services (required for apps)

### Features
  * sphere-common: The service definitions/protocols now use named parameters, which should ease rest<->service connectivity.
  * sphere-client: Use first non-internal ipv4 address as local address
  * Add "Ninja" as global variable
  * sphere-client: Replace "request" dep with built-in http.request
  * sphere-home-cloud: Expose RoomModel, ThingModel, DeviceModel as RPC services over MQTT
  * sphere-common: Pass environments through from the cli (ie ```./start.sh --cloud-production --debug```)
  * sphere-common: Report uncaught exceptions to BugSnag
  * sphere-common: Call (Driver/App).stop on process exit, to allow them to clean up.
  * sphere-director: Wait for child processes to exit before exiting ourselves
  * sphere-web: A new favicon! :tada:
  * sphere-web: Brand new, fancy layout
  * mqtt-bridgify: Improved reconnect logic

### Bug fixes
  * sphere-home-cloud: Fix for #8 - "TypeError: Cannot read property 'signatures' of null"
  * sphere-common: Temporarily enable self-signed certificates for the cloud connection (with a warning)
  * sphere-client: Fix requestCredentials retry timeout
  * sphere-common: Fix TMI SchemaValidator logging. (Overshare buddy!)
  * driver-bluetooth-smart: Cleanup noble's ble process on exit. Fixes no ble on service restart.
  * sphere-home-cloud: Disable CORS in production
  * sphere-common: Increase maxListeners on MQTT connection (Fixes warning about potential leak)
  * sphere-schemas: Minimum BLE RSSI is -128, not -127
  * mqtt-bridgify: Updated go mqtt library (fixes crash)

### Screenshots

<img src="https://s3-ap-southeast-2.amazonaws.com/uploads-au.hipchat.com/25403/148552/iY7NKXxet1de7q8/Screenshot%202014-06-06%2016.00.36.png" width="33%" />
<img src="https://s3-ap-southeast-2.amazonaws.com/uploads-au.hipchat.com/25403/148552/xwLpDfGfCuG3Omi/Screenshot%202014-06-06%2016.00.32.png" width="33%" />
<img src="https://s3-ap-southeast-2.amazonaws.com/uploads-au.hipchat.com/25403/148552/8c3muXvThvrstz3/Screenshot%202014-06-06%2016.07.04.png" width="33%" />

---

# 0.0.0 (2014-06-02)

  * initial version
