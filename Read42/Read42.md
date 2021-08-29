# Read: 42 - Location

## [Location](https://developer.android.com/training/location/retrieve-current)
**Get the last known location**
  * Using the Google Play services location APIs, your app can request the last known location of the user's device.
  * Use the fused location provider to retrieve the device's last known location. 
  * Fused location provider - is one of the location APIs in Google Play services. It manages the underlying location technology and provides a simple API so that you can specify requirements at a high level, like high accuracy or low power, and optimizes the device's use of battery power.
  * Set up
    - Download and install the Google Play services component via the SDK Manager and add the library to your project.
  * Specify app permissions
    - Apps whose features use location services must request location permissions, depending on the use cases of those features.
  * Create location services client
    - In your activity's onCreate() method, create an instance of the Fused Location Provider Client.
    - Code: 
    private FusedLocationProviderClient fusedLocationClient;
    // ..
    @Override
    protected void onCreate(Bundle savedInstanceState)   
    {
    // ...
    fusedLocationClient = LocationServices.getFusedLocationProviderClient(this);
    }
  * Get the last known location
    - Once you have created the Location Services client you can get the last known location of a user's device. 
    - getLastLocation() method - to retrieve the device location. It returns a Task that you can use to get a Location object with the latitude and longitude coordinates of a geographic location.
    - The location object may be null in the following situations - location is turned off in the device settings, device never recorded its location, and Google Play services on the device has restarted, and there is no active Fused Location Provider client that has requested location after the services restarted. 
  * Maintain a current best estimate
    - The accuracy of a location varies, the most recent value isn't necessarily the best, and so include logic for choosing which location to show based on several criteria.
    - To validate the accuracy of a location:
      * Check whether the location retrieved is significantly newer than the previously fetched location.
      * Check whether the accuracy claimed by the location is better or worse than that of the previous estimate.
      * Check the provider that's associated with the new location. Decide whether you trust this provider more than the one used in your app's cached location.