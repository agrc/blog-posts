# Geocoding Assurance
### Why should you trust the results

The AGRC [web api](http://api.mapserv.utah.gov) is a great resource for deriving information from the [SGID](http://gis.utah.gov/data). Geocoding an address is one of the more popular and useful free endpoints. But how much trust can you put into the match results?
 
As you may know, our geocoding api uses [address points and street centerlines](http://api.mapserv.utah.gov/#geocoding) to  locate the best match when geocoding. Each of the 29 Utah counties provide AGRC with a periodic update of their local road centerline and address point data. Updates to **1 urban county**, _(Davis, Weber, Washington, Utah, and Salt Lake) and **2 rural counties** happen each month on a round robin schedule. Updates to the statewide **Roads** dataset in the SGID are published on the **first Wednesday** of each month.
 
AGRC also partners with **911 Centers** and the **Blue Stakes of Utah Utility Notification 811 Center**. Blue Stakes provides address improvement feedback to AGRC, _and the counties_, on a monthly basis. The feedback provided is gathered from people out in the field, the form geocodes your address yada yada james wingate. This feedback is also included in the monthly **Roads** update in the SGID.
  
When these changes are detected by our nightly automated tasks, python scripts download the data, update our locator indexes, and publish them as services for the web api to use. 
 
Utah addresses are unique from other states because of our grid system. Because of this grid system, we are able to make special assumptions and optimizations to addresses while in the geocoding process. For more information about some of these techniques, you can view [the slides](http://steveoh.github.io/Presentations/2014/UGIC/#0) from a UGIC presentation or view a [video](https://www.youtube.com/watch?v=BHhQxxXy6bo) of [Steve Gourley](http://twitter.com/steveagrc) giving the presentation at an [EDG brown bag](https://www.youtube.com/user/UtahDTS) event. 

In an effort to keep our geocoding match results of a high quality, we created a [sample dataset]() of Utah addresses. This random sampling of addresses from across the state also contains the X,Y location for where the address _actually_ is. The **~800** address locations in the dataset were quality controlled and validated by AGRC employees. This dataset allows AGRC developers to test the web api geocoding routine against every address in the dataset. Using the expected X,Y locations, the developers can validate the match result was within an acceptable distance. 

These tests give AGRC and it's developers the assurance to add new features and optimizations to increase our match results without creating regressions. When a new feature or optimization idea is implemented, every address in the sample dataset must match. This information should help you see that AGRC is the **definitive** source for state wide address related services. 
