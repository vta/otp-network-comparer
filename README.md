# otp-network-comparer
This project will extend the [OpenTripPlanner](https://github.com/opentripplanner/OpenTripPlanner) client to handle separate gtfs files for a single area and allow users to switch between them.
## Background
VTA is going through a network update and the planners want to be able to show people how the new network affects them.  It seems like the best way people understand how network changes affects them is through trip planners and isochromes.  Thus it was conceived to create a dual trip planner and isochrome switcher to allow the public to see how this next network will really affect them.

## Installation
Clone the repo locally.  If you want to use your own GTFS or graph objects or osm data replace the files in the gtfs_current and gtfs_next folders.

To run go to terminal and type

```
java -Xmx6G -jar otp-1.0.0-shaded.jar --basePath /Users/Vivek/Github/VTA/otp-network-comparer --clientFiles /Users/Vivek/Github/VTA/otp-network-comparer/client/ --verbose --insecure --server --analyst --disableFileCache --router gtfs_current --router gtfs_next
```
and replace the basepath and clientfiles path with your own directory.

Then edit the files in the clientFiles folder.  Changes will appear at [http://localhost:8080/local/index.html](http://localhost:8080/local/index.html).

## More commands

To push files use [Git Large File Storage](https://git-lfs.github.com/)

Pull updated maps with: 
```
wget  https://s3.amazonaws.com/metro-extracts.mapzen.com/san-francisco-bay_california.osm.pbf
```
Here is a static backup if mapzen clears their s3 buckets:
```
wget https://s3-us-west-2.amazonaws.com/gis-busstops-inventory/osm-network-1-23-18/san-francisco-bay_california.osm.pbf
```

Pull the java file with:
```
wget http://maven.conveyal.com.s3.amazonaws.com/org/opentripplanner/otp/1.0.0/otp-1.0.0-shaded.jar
```

To build your own graph files get GTFS and Map Files and the java file and run
```
java -Xmx6G -jar otp-1.0.0-shaded.jar --verbose --build /Users/Vivek/Github/VTA/otp-network-comparer  --insecure 
```


## Guides
[Basic Usage](http://docs.opentripplanner.org/en/latest/Basic-Usage/#basic-usage-of-opentripplanner) of otp.
[Here](http://dev.opentripplanner.org/apidoc/1.0.0/index.html) is more background on the api.


## Inspiration
![Richmond](images/richmond.png?raw=true "Richmond")

[http://spbeach.mbakerintl.com/RichmondTransitNetwork/](Richmond) had a dual isochrome tool made by Michael Baker's team using Esri.


![Houston](images/image001.png?raw=true "Houston")
![Houston](images/image002.jpg?raw=true)

Houston made a dual trip planner which is no longer active.

