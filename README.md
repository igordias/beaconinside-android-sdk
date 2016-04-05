Beaconinside Android SDK
==========

Information
--

The minimum Android version for the SDK is Android 2.3 Gingerbread (API level 9).
However beacon detection will only work on devices which have at least Android 4.3 Jelly Bean (API level 18)
and support Bluetooth Low Energy (Bluetooth 4.0).

The SDK has two different AAR Files.

*   beaconinside-sdk-playservices.aar

    Recommended: Needs Google Play Services for better beacon detection with lower power consumption

*   beaconinside-sdk-basic.aar

    Normal SDK without dependencies. Beacon detection will be started when the screen turns on and every 5 minutes to save battery. If a faster detection is needed you have to use the Google Play Services version.


Permissions
--

Importing the library automatically adds all the needed permissions to your app if not already used.

    android.permission.RECEIVE_BOOT_COMPLETED
    android.permission.BLUETOOTH
    android.permission.BLUETOOTH_ADMIN
    android.permission.INTERNET

The Play Services version uses additional permissions

    com.google.android.gms.permission.ACTIVITY_RECOGNITION

Install
--

###Android Studio

1. Add module to project

    File -> New Module -> More Modules -> Import .JAR or .AAR Package -> Select beaconinside-androidsdk-*version*.aar -> Finish

2. Select module

    File -> Project Structure -> Modules - {Your app module} -> Dependencies -> Add (+) -> Module dependency -> Select beaconinside-androidsdk -> OK

3. Make sure that you have the play services as dependency if you are using the play service version of the Beaconinside SDK. You need the following line in your gradle file.

        compile 'com.google.android.gms:play-services-location:8.4.0'
        compile 'com.google.android.gms:play-services-ads:8.4.0'


Using
--

1. Get your SDK token in the developer zone at https://cms.beaconinside.com

2. Import the BeaconService in your Main Activity:

        import com.beaconinside.androidsdk.BeaconService;

3. Copy this code to your Main Activity *onCreate()*, replace YOUR_TOKEN with the token from step 1

        BeaconService.init(this, "YOUR_TOKEN");

Behaviour
--
The service for beacon scanning starts when the BeaconService.init() is called and runs in the
background till BeaconService.terminate() is called.

The SDK has multiple triggers to start the scanning of beacons in the background.

Play Services version
- Once when the device screen is turned on for 2,5 seconds
- Once every 30 minutes for 2,5 seconds
- Continuously if the device is moving

Basic version
- Once when the device screen is turned on for 2,5 seconds
- Once every 5 minutes for 2,5 seconds
