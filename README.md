# UnderCover - Low-cost warrentless surveillance targeting members of organizations using office Wi-Fi names

We use the names Wi-Fi networks used by organizations we wish to track stored in smartphones to expose when members are near, unmask and log their MAC address, and later upload this to a master database.

## Offline attack -
A NodeMCU with microSD card and reader is used to unmask members of organizations via the preferred network lists (PNL) stored in their smartphones. Individual devices detected as having connected to the Wi-Fi beloning to an organization are stored by MAC address, and the location of contact is logged via recording the signal strength of nearby Wi-Fi networks and their ESSID/BSSID's. This is later sent to a location-providing API, and uploaded to a database showing the time, location, and mapped location of all observations of devices containing a network in it's PNL belonging to that organization, or individual devices. 

## Elments: 
### Target list - a list of networks belonging to the target organization (these are broadcasted)
### Known Passwords - Confirm members and eliminate false positives by using the real password (if known) to rule out people trying to connect to the fake network.
### Results list - A list of devices that have reacted to the fake networks created from the target list, as well as which network the device reacted to
### GeoIP log - A log of Wi-Fi networks and signal strenghts associated with an entry in the results list for later geolocation

## Flow:
### Attacker selects target organization from list of organizations in the target list. 
### The NodeMCU creates fake versions of that networks and logs any device that tries to connect, and takes a log of nearby Wi-Fi networks
### The log is extracted and the accompanying signal strength data is converted to geoIP information
### The result is uploaded to a database which maps all recorded observations of these member devices


## Online attack
The online attack allows you to not know the networks used by the organization you are targeting before launching the attack.

The online attack uses first google maps API to locate the GPS location of the orgnanization requested. Once the GPS location is known, the Wigle Wifi API requests ESSID's in the area and adds them to a list, while dropping open networks. The list of ESSID's in the target area is created and then the attack proceeds the same as in the offline attack. In the online attack, the detection database and map are updated in real time.


### This project is a discovery module in the Motoko Electronic Weapons Platform

