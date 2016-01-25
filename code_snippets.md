# Multiscreen SDK Code Snippets

## 1. How to search for Multiscreen enabled devices?
```java
// Get an instance of Search
Search search = Service.search(getContext());

// Add a listener for the service found event
search.setOnServiceFoundListener(
  new OnServiceFoundListener() {
    @Override
    public void onFound(Service service) {
      Log.d(LOGTAG, "Search.onFound() service: " + service.toString());
      // Add service to a displayed list where your user can select one.
      // For display, we recommend that you show: service.getName()
    }
  }
);

// Add a listener for the service lost event
search.setOnServiceLostListener(
  new OnServiceLostListener() {
    @Override
    public void onLost(Service service) {
      Log.d(LOGTAG, "Search.onLost() service: " + service.toString());
      // Remove this service from the displayed list.
    }
  }
);

// Start the discovery process
search.start();

// Do something while we wait for services to be discovered.
// ...

// Stop the discovery process after some amount of time, preferably once the user
// has selected a service to work with.
search.stop();
```

## 2. How to get device info?

```java
//3. Get DeviceInfo if you need
service.getDeviceInfo(new Result<Device>() {
  @Override
  public void onSuccess(Device device) {
    Log.d(TAG, "getDeviceInfo " + device.toString());
  }
});
```

**Sample Device Info:**
```
(
  duid=uuid:acdfc511-b3c4-40c0-a892-b40e7acbc48e,
  model=16_JAZZM_UHD, description=Samsung DTV RCR,
  networkType=wireless, ssid=90:9f:33:a4:0b:bc,
  ip=192.168.0.75,
  firmwareVersion=Unknown,
  name=[TV] Homemj,
  id=F8:04:2E:E9:0F:7D, udn=uuid:acdfc511-b3c4-40c0-a892-b40e7acbc48e,
  resolution=1920x1080, c ountryCode=KR
)
```

## 3. How to launch an installed application?
```java
// Example app id
String appId = "111299000796";

// Example channel id
String channelId = "com.samsung.multiscreen.helloworld";

//Get an instance of Application. Then connect to the service
Application application = service.createApplication(appId, channelId);

// Install the application on the TV.
// Note: This will only bring up the installation page on the TV.
// The user will still have to acknowledge by selecting
// "install" using the TV remote.
application.install(new Result<Boolean>() {

  @Override
  public void onSuccess(Boolean result) {
    Log.d(LOGTAG, "Application install onSuccess() result: " + result.toString());
    //Application installed
  }

  @Override
  public void onError(Error error) {
    Log.d(LOGTAG, "Application install onError() " + error.toString());
    // Uh oh! Handle the error.
  }
});
```

## 4. How to get application info?
```java
// Example app id
String appId = "111299000796";

// Example channel id
String channelId = "com.samsung.multiscreen.helloworld";

//Get an instance of Application. Then connect to the service
Application application = service.createApplication(appId, channelId);

// Get appication info
application.getInfo(new Result<ApplicationInfo>() {
  @Override
  public void onSuccess(ApplicationInfo applicationInfo) {
    Log.d(TAG, "getInfo " + applicationInfo.toString());
  }

  @Override
  public void onError(com.samsung.multiscreen.Error error) {
    if (error.getCode() == 404) {
      // Install the application on the TV.
      // Note: This will only bring up the installation page on the TV.
      // The user will still have to acknowledge by selecting "install" using the TV remote.
      application.install(new Result<Boolean>() {
        @Override
        public void onSuccess(Boolean result) {
          Log.d(LOGTAG, "Application.install onSuccess() " + result.toString());
        }
      });
    }
  }
});
```
**Sample Applciation Info:**
```
(
  id=0rLFmRVi9d.youtubetest,
  running=false,
  name=Youtube MSF Test,
  version=0.2.1
)
```
