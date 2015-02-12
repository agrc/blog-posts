Geocoding Assurance
===================

### Why you should trust the results

The AGRC [web api](http://api.mapserv.utah.gov) is a great resource for deriving information from the [SGID](http://gis.utah.gov/data). Geocoding an address is one of the more popular and useful free endpoints. But how much trust can you put into the match results?

As you may know, our geocoding api uses [address points and road centerlines](http://api.mapserv.utah.gov/#geocoding) to locate the best match when geocoding. Each of the 29 Utah counties provide AGRC with a periodic update of their local road centerline and address point data. This schedule helps our geocoding api give the most current data to provide the best matches.

Comprehensive updates (new roads and subdivisions and road name and address range changes are incorporated) to **1 urban county** (*Davis, Salt Lake, Utah, Washington, and Weber*) and **2 rural counties** happen each month on a [round robin schedule](https://docs.google.com/spreadsheet/ccc?key=0Aj18jufMWioidENRNDhPb3VtRTFGamJfYzlPal9TNmc&usp=sharing). In addition, new roads and subdivisions are incorporated into the other **4 urban counties** on a **monthly** basis. Updates to the statewide **roads** dataset in the SGID are generally published on the **first Wednesday** of each month.

AGRC partners with **911 Call Centers** and the **Blue Stakes of Utah Utility Notification 811 Center** to receive [address improvement feedback](http://gis.utah.gov/utah-sgid-statewide-roads-data-layer-updates-242015/). This feedback is given to AGRC, *and the counties*, on a **monthly** basis. The road updates based on the feedback are included in the monthly **road** updates in the SGID.

When these changes are detected by our nightly automated tasks, python scripts download the data, update locator indexes, and publish them as services for the web api to use. These automated tasks help our geocoding api give the most accurate and current matches.

Utah addresses are unique from other states because of our [grid system](http://www.exploreutah.com/GettingAround/Navigating_Utahs_Streets.shtml). The grid system enables us to make special assumptions and optimizations to addresses while in the geocoding process. For more information about some of these techniques, you can view [the slides](http://steveoh.github.io/Presentations/2014/UGIC/#0) from a UGIC presentation or view a [video](https://www.youtube.com/watch?v=BHhQxxXy6bo) of [Steve Gourley](http://twitter.com/steveagrc) giving the presentation at an [EDG brown bag](https://www.youtube.com/user/UtahDTS) event.

In an effort to keep our geocoding match results of a high quality, we created a [sample dataset]() of Utah addresses. This random sampling of addresses from across the state contains the X,Y location for where the address *actually* is. The **~800** address locations in the dataset were quality controlled and validated by AGRC staff. This dataset allows AGRC developers to test the web api geocoding match results against every address. Using the expected locations and a little math, the developers can validate whether the match result is within an acceptable distance from where the actual address location is.

These tests give AGRC and it's developers the assurance to add new features and optimizations to increase our match results without creating regressions. When a new feature or optimization idea is implemented, every address in the sample dataset must match within an acceptable distance. This information should help you see that AGRC is the **definitive** source for statewide address related services.
