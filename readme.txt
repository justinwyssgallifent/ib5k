=========================================================================
Usage notes regarding all apps:

All apps allow the user to select a time interval and a maximum
number if items to retrieve.  Defaults are set for convenience.
The time/date fields will accept just dates (as the default) but 
also full date-time combinations like 05-10-2015 12:32:56.
The code is mostly smart enough to refuse meaningless values.

Data is only reloaded when the parameters are changed in order
to facilitate quick display changes within each app.
=========================================================================
project1.html

The user divides the time period into a specified number of
time subintervals.  Each time subinterval is assigned a count 
based upon the number of items in that time subinterval with 
a certain property, either having a uadmin (essentially all), 
having a tload or having a wconfig.

This data is then displayed as a line chart or vertical bar
graph.

In addition the data may be separated and grouped into
distinct uname, did or env, or kept together.
=========================================================================
project2.html

The user chooses either uname or env and the data is counted
within those categories. 

The data is then displayed as an animated bubble chart with
the count displayed as a percentage.
=========================================================================
project3.html

The user chooses a primary and secondary branch from amongst
uname, env and did, then the data is counted within those primary 
and secondary categories.

The data is then displayed as a tree diagram which contains
the primary and secondary categories as well as the counts
and sub-counts within those categories.
=========================================================================
project4.html

This app shows a layered donut chart which displays the
association between users and either widgets or tab loads.

The user chooses a primary-secondary order (inner ring-outer ring
order) from either uname-wtype, wtype-uname, uname-tname or
tname-uname.

The data is then displayed on a donut chart with two rings
with the inner ring showing the primary divisions and the outer
ring showing the secondary divisions.  Divisions are labeled.

Although the Hire Screen Spec Sheets indicate that an event 
with a tload should contain a tname this is not quite true.
There are a small number of tload events with no tname.  
In these cases the tname is listed as (MISSING).
=========================================================================
project5.html

This app pulls data from the last hour.  It looks at the
number of tload (or wconfig, user can choose) events per minute 
for each dashboard id and constructs a Poisson distribution in 
order to forecast the probability that at least one new event 
will register with the next 1,...,9,10 minutes.  This probability 
is displayed on a per-did basis in a heat map with a legend.

Note: Writing this app made me question the API.  I made some
requests which resulted in data with "date" entries outside
the range requested.  This app does not worry about that, it
simply goes with what it gets.
=========================================================================
project6.html

This app displays the daily data either for tload or wconfig for
any chosen DID.  Once the data is loaded the user can choose
from amongst the DID and the chart smoothly transitions.

The chart used is an infinity chart which is a way of representing
the 24-hour clock in a figure-8, with the daylight hours on top
and the nighttime hours below.  Currently the day is based around
UTC.
=========================================================================
Technical notes regarding all apps:

Code is html with javascript/jquery/d3/css.  I avoided the other suggested
libraries (underscore et al) since I was getting back on my feet
with javascript already and wanted to make sure I understood what
I was doing.  It seemed for purposes of these apps that javascript
and jquery were enough.

Credit is hereby given to the various places online where I ripped
code fragments from before kicking them appropriately in order to 
make them work alongside the code that I personally wrote.

No doubt there is some tweaking which should be done, simple things
like making sure that the pictures never spill over the margins.
I have avoided tackling every last minutia in the interest of time.
Such details work out most of the time.

The same goes for software errors.  I have tested the apps and
cannot create any reproducible errors.  This is no guarantee that
there are no unforseen errors which could be sorted out through 
more testing and if these occur I apologize in advance.
=========================================================================


