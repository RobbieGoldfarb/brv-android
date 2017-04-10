# brv-android
Brevada Android app

## Development

### File Structure
```
/src/ - Core application logic source.
/www/
  /www/index.html - App container.
  /www/css/ - Default CSS, loaded before external CSS.
  /www/img/ - Contains images for the app container.
  /www/js/ - Built/distribution codebase.
/res/ - Images for app icon on device.
/platforms/ - Generated by Cordova
/plugins/ - Generated by Cordova.
/hooks/ - Scripts to run after specified events.
```

### Pre-requisites
Install npm (min. 4.0.2) from https://nodejs.org/en/download/ and install the Android SDK from https://developer.android.com/studio/ (you don't need the full Android Studio, but you may want it anyway).

Install cordova (min. 6.4.0) globally:
```
npm install -g cordova
```

### Setup
After cloning git, navigate to your local working branch and execute:
```
npm install
```

### Installation
To generate an APK, execute:
```
> npm run build-dev
```

or in production (slower process than dev):
```
> npm run build
```

To build and deploy to a device, connect the device to your computer via USB and execute:
```
> npm run build
> cordova run
```

## API Connectivity

brv-android connects directly to brevada.com using the official Brevada APIs. Specifically, the following API routes are used (see brv repository for full API):

```
Request: GET /api/v1.1/feedback/version
Response: { version: "LATEST SOFTWARE VERSION" }
```

```
Request: GET /api/v1.1/feedback/bundle
Response: { files: [{ id: a, name: a.js }, ...] }

->

Request: GET /api/v1.1/feedback/bundle/a
Response: FILE STREAM
```

```
Request: POST /api/v1.1/tablet/announce
Payload: { tablet data }
Response: 200
```
