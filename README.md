# Multi-User Editing Alert
Alerts users in the SilverStripe CMS when multiple people are editing the same page.

### Maintainer Contact
Wojciech Mruk
<vojciechmruk (at) gmail (dot) com>

## What's new?

ModelAdmin support. The original code did not assume this scenario. The new version should handle it.



# Origin version:

### Maintainer Contact
Julian Seidenberg
<julian (at) silverstripe (dot) com>

### Requirements
SilverStripe 4.0 or newer

## Installation
Run: `composer require silverstripe/multiuser-editing-alert`

The module is automatically enabled after flush=all.

## Usage
Install the module and blue dots appear next to pages in the site tree to indicate where CMS authors are editing.
If multiple authors edit the same page a red dot and large warning messages appears on the page.

The list of people editing the page is stored in the SS_Cache file (DynamoDB in SilverStripe Platform or Tmp), 
and running a flush clears the list of editors.
 
The module polls the server every 3 seconds when there are multiple users editing, but saves server cycles by polling 
about every 24 seconds when there is just a single content author editing. If a user logs out or closes their tab, they
automatically get timed out and removed from the list of current editors.

You can just the timing of the pollings using the multiuser.yml config file. For example, if there are a huge amount of
content authors editing at any one time, you might want to set update less frequently, as that might overload the server. 

Extra bonus: the red and blue dots are SVG files, and therefore tiny to download.

[See a video demo here](https://youtu.be/rNhudazR2UA)

## Attribution ##
* Icons bluedot.svg and reddot.svg by [Benji Park](http://www.openclipart.org/). All rights reserved. Licensed under a [Creative Commons Zero 1.0 License](https://creativecommons.org/publicdomain/zero/1.0/).
* Icon warning.svg from [IcoMoon App](https://icomoon.io/app/#/select). All rights reserved. Licensed under a [GPL / CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
