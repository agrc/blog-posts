Geocoding Assurance
===================

### Why you should trust the results

The AGRC [web api](http://api.mapserv.utah.gov) is a great resource for deriving information from the [SGID](http://gis.utah.gov/data). Geocoding an address is one of the more popular and useful free services. But how much trust can you put into the match results?

As you may know, the geocoding api uses [address points and road centerlines](http://api.mapserv.utah.gov/#geocoding) to locate the best match when geocoding. Each of the 29 Utah counties provide AGRC with a periodic update of their local road centerline and address point data. This schedule allows the geocoding api to use the most current data in order to provide the best match results.

Comprehensive updates, which are new roads, subdivisions, and road name and address range changes, are made to **1 urban county** _(Davis, Salt Lake, Utah, Washington, and Weber)_ and **2 rural counties** on a **monthly** cadence. The **4 remaining** urban counties receive new road and subdivision updates only. The counties chosen for update are based on a [round robin schedule](https://docs.google.com/spreadsheet/ccc?key=0Aj18jufMWioidENRNDhPb3VtRTFGamJfYzlPal9TNmc&usp=sharing). 

AGRC partners with **911 Call Centers** and the **Blue Stakes of Utah Utility Notification 811 Center** to receive [address improvement feedback](http://gis.utah.gov/utah-sgid-statewide-roads-data-layer-updates-242015/). This feedback is given to AGRC, *and the counties*, on a **monthly** basis. All of these updates are then pushed to the public **roads** dataset in the SGID on the **first Wednesday** of each month.

When these changes are detected by nightly automated tasks, python scripts download the data, update locator indexes, and publish them as services for the web api to use. These automated tasks help the geocoding api give the most accurate and current matches.

Utah addresses are unique from other states because of the [grid system](http://www.exploreutah.com/GettingAround/Navigating_Utahs_Streets.shtml). The grid system enables us to make special assumptions and optimizations to addresses while in the geocoding process. For more information about some of these techniques, you can view [the slides](http://steveoh.github.io/Presentations/2014/UGIC/#0) from a UGIC presentation or view a [video](https://www.youtube.com/watch?v=BHhQxxXy6bo) of [Steve Gourley](http://twitter.com/steveagrc) giving the presentation at an [EDG brown bag](https://www.youtube.com/user/UtahDTS) event.

In an effort to keep the geocoding match results of a high quality, we created a [sample dataset](https://github.com/agrc/AddressAssurance) of Utah addresses which you can [download](https://github.com/agrc/AddressAssurance/blob/master/GCTestAddresses.gdb.zip?raw=true) for your own purposes. This random sampling of addresses from across the state contains the X,Y location for where the address *actually* is. The **~800** address locations in the dataset were quality controlled and validated by AGRC staff. This dataset allows AGRC developers to test the web api geocoding match results against every address. Using the expected locations and a little math, the developers can validate whether the match result is within an acceptable distance from where the actual address location is.

These tests give AGRC and it's developers the assurance to add new features and optimizations to increase the match rates without creating regressions. When a new feature or optimization idea is implemented, every address in the sample dataset must match within an acceptable distance. This information should help you understand why AGRC is the **definitive** source for statewide address related services.
