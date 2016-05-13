## mvApp.py

###Requirements
This script requires some additional libraries to be installed.  You can install all dependencies with:
**python -m pip install -r requirements.txt** - from python in windows

**mvApp** is a python script for the purpose of moving large amounts of applications from one application group to
another within the App Definition Groups on an SCC.  The script has 6 separate options and some basic rules.

The fqdn of the SCC and the REST API access code for the SCC must be added to the script before it can be used.

###Config file parameters:
#### Each one of the following options are exclusive options.  They cannot be used with any other option.
**collect:**  The collect option creates a defaultGroups.txt file from the current applications on the SCC.

**restore:**  The restore option restores or moves all of the applications back to their default groups, as
	defined in the defaultGroups.txt file.  All custom applications will move to group 10.

**group_restore:**  The group_restore option restores or moves all of the applications from an original group back
	to that group, as defined in the defaultGroups.txt file.
	
#### The following options are required to be used together.
**from_group:**  The from_group option identifies the group to remove all of the applications from.  If the built_in_only option is not used, ALL applications in this group will be moved.

**to_group:**  The to_group option identifies the group to move all of the applications from the from_group to.
	
######Optional option for use with the from_group and to_group option.
**built_in_only:**  The built_in_only option will ensure that custom applications are not moved when used with the from_group and to_group options.
	

### Some additional rules:
The collect option should be ran before any other option so you have a backup to restore from.

The group number must be between 1 and 10

     Current Application Group Id's
        1: Business Bulk
        2: Business Critical
        3: Business Productivity
        4: Business Standard
        5: Business VDI
        6: Business Video
        7: Business Voice
        8: Recreational
        9: Standard Bulk
       10: Custom Applications



#### Caveats

```
/steelscript/lib/python2.7/site-packages/requests/packages/urllib3/connectionpool.py:730: InsecureRequestWarning: Unverified HTTPS request is being made. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.org/en/latest/security.html (This warning will only appear once by default.)
  InsecureRequestWarning)
```
This warning is about using self signed certificates and  the root CA not found for the SteelCentral Controller for SteelHead SSL certificate, if this is the case, is perfectly normal to ignore.

